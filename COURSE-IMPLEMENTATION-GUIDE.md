# Production Engineering Implementation Guide

**Applies to:** Lessons 36–48  
**Purpose:** Turn the production-engineering lessons into a reproducible local path. This guide supplements the daily lessons; it does not claim that a lab has been executed on your machine.

## One consistent lab target

Use one small FastAPI service as the learning target. Do not try to retrofit every exercise into all three portfolio projects at once.

Suggested layout:

```text
production-lab/
├── app/
│   └── main.py
├── monitoring/
│   ├── prometheus.yml
│   ├── alerts.yml
│   └── alerts.test.yml
├── tests/
│   └── test_health.py
├── Dockerfile
├── compose.yaml
├── requirements.txt
└── .dockerignore
```

Start with the smallest working service, then add one operational capability per lesson. When a capability is stable, port it into the relevant flagship project using the mapping in [PROJECT-DELIVERY-MAP.md](PROJECT-DELIVERY-MAP.md).

## Day 36 — Metrics: a working FastAPI target

Install:

```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# macOS/Linux:
# source .venv/bin/activate
python -m pip install fastapi "uvicorn[standard]" prometheus-client httpx pytest
```

Create `app/main.py`:

```python
import time
from fastapi import FastAPI, Request
from fastapi.responses import Response
from prometheus_client import Counter, Histogram, generate_latest, CONTENT_TYPE_LATEST

app = FastAPI()

REQUESTS = Counter(
    "http_requests_total",
    "Completed HTTP requests",
    ["method", "route", "status_class"],
)
DURATION = Histogram(
    "http_request_duration_seconds",
    "HTTP request duration in seconds",
    ["method", "route"],
)

@app.middleware("http")
async def observe_requests(request: Request, call_next):
    started = time.perf_counter()
    route = request.url.path
    status_code = 500
    try:
        response = await call_next(request)
        status_code = response.status_code
        return response
    finally:
        # Avoid raw IDs and query strings in labels: they create high cardinality.
        matched_route = request.scope.get("route")
        route_label = getattr(matched_route, "path", route)
        status_class = f"{status_code // 100}xx"
        REQUESTS.labels(request.method, route_label, status_class).inc()
        DURATION.labels(request.method, route_label).observe(
            time.perf_counter() - started
        )

@app.get("/health")
async def health():
    return {"status": "ok"}

@app.get("/work")
async def work():
    time.sleep(0.02)  # Deliberate blocking example; remove in a real async route.
    return {"result": "done"}

@app.get("/fail")
async def fail():
    raise RuntimeError("deliberate test failure")

@app.get("/metrics")
async def metrics():
    return Response(generate_latest(), media_type=CONTENT_TYPE_LATEST)
```

The deliberate `time.sleep` demonstrates why blocking work should not run inside an async endpoint. It is not a recommended production implementation. For the exception path, FastAPI's exception middleware returns a 500 response; the metrics middleware records the default 500 status.

Run:

```bash
uvicorn app.main:app --reload
```

In another terminal:

```bash
curl http://127.0.0.1:8000/health
curl http://127.0.0.1:8000/work
curl http://127.0.0.1:8000/fail
curl http://127.0.0.1:8000/metrics
```

Expected observations:
- `http_requests_total` increases after each request.
- `http_request_duration_seconds_bucket` and `_count` appear.
- The failed route is counted as a 5xx response.
- Route labels use route templates where FastAPI has resolved them. Never add user IDs, request IDs, arbitrary URLs, or query strings as metric labels.

A useful test is to call `/health` twice and `/fail` once, then inspect the corresponding counters. Metrics are process-local in this simple example; multi-worker deployments need a deliberate Prometheus Python client multiprocess configuration.

## Day 37 — Prometheus scrape and alert tests

Create `monitoring/prometheus.yml`:

```yaml
global:
  scrape_interval: 5s
scrape_configs:
  - job_name: rag-api
    static_configs:
      - targets: ["api:8000"]
```

Create `monitoring/alerts.yml`:

```yaml
groups:
  - name: rag-api
    rules:
      - alert: HighServerErrorRate
        expr: |
          sum(rate(http_requests_total{status_class="5xx"}[5m]))
          / clamp_min(sum(rate(http_requests_total[5m])), 1) > 0.05
        for: 2m
        labels:
          severity: warning
        annotations:
          summary: "RAG API server error ratio is elevated"
      - alert: HighP95Latency
        expr: |
          histogram_quantile(
            0.95,
            sum by (le) (rate(http_request_duration_seconds_bucket[5m]))
          ) > 1
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "RAG API P95 latency is elevated"
```

These are demonstration thresholds, not production SLOs. The error-rate denominator must represent the same request population as the numerator. A real service should define an SLO from user impact and sufficient traffic volume, then test alert noise and detection delay.

For a reproducible local stack, add Prometheus to Compose:

```yaml
  prometheus:
    image: prom/prometheus:latest
    ports:
      - "9090:9090"
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml:ro
      - ./monitoring/alerts.yml:/etc/prometheus/alerts.yml:ro
    depends_on:
      - api
```

Add `rule_files: ["/etc/prometheus/alerts.yml"]` under the top-level Prometheus configuration. In the Compose network, the target is `api:8000`, not `localhost:8000`. For reproducible deployment, pin a tested Prometheus image version or digest rather than using `latest`.

Validate rules with:

```bash
promtool check rules monitoring/alerts.yml
```

If Prometheus is running in a container, run `promtool` in that container or use a matching local Prometheus release. For deterministic rule behavior, add Prometheus rule unit tests and run `promtool test rules monitoring/alerts.test.yml`. Test both a healthy series and a sustained breach; YAML parsing alone is not proof that the expression measures the intended population.

## Day 38–40 — Container → Compose → CI

Keep the same service entrypoint throughout the three days:

- Python import path: `app.main:app`
- Container port: `8000`
- Health endpoint: `/health`
- Metrics endpoint: `/metrics`

Dockerfile:

```dockerfile
FROM python:3.12-slim
ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app ./app
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Use a `.dockerignore` that excludes `.git`, `.venv`, `__pycache__`, `.env`, test caches, and local secrets. Never copy a real `.env` into the image. For production, lock dependencies, use a non-root user, scan the image, and pin a verified base image.

A Compose healthcheck for the API can use Python's standard library:

```yaml
services:
  api:
    build: .
    ports:
      - "8000:8000"
    healthcheck:
      test: ["CMD", "python", "-c", "import urllib.request; urllib.request.urlopen('http://127.0.0.1:8000/health')"]
      interval: 10s
      timeout: 3s
      retries: 5
```

Run `docker compose config --quiet`, `docker compose up --build -d`, `docker compose ps`, and `docker compose logs -f api`. Confirm the health status becomes healthy. Do not use `down -v` unless you intentionally want to delete named volumes.

For CI, separate untrusted PR verification from trusted publishing:
- PR: checkout, build, test, scan; no registry write permission and no publishing credentials.
- Protected main-branch push: build, scan, then publish with only the permissions required.
- Pin third-party actions to reviewed full commit SHAs in a security-sensitive repository. If using major tags for a learning exercise, record that they are mutable references and verify current releases before copying them.

The image tag should include an immutable identifier such as the commit SHA. Normalize the GHCR image name to lowercase before publishing. Do not assume `${{ github.repository }}` is lowercase.

## Day 41 — Security scan as a release gate

The order is **build → scan → publish**, not publish → scan. Keep a report artifact for every release candidate. Record:
- image digest and source commit;
- scanner version and scan date;
- CRITICAL/HIGH findings, fixed versions, and whether a fix exists;
- accepted exceptions, owner, rationale, and review date.

A scanner finding is not proof of exploitability, and a clean report is not proof of security. Do not silently suppress findings. Make the gate policy explicit and test that a deliberately vulnerable test image fails the pipeline.

## Day 42 — API structure and test boundary

Use a small structure, not a large architecture ceremony:

```text
app/
├── main.py
├── core/config.py
├── api/routes/
├── schemas/
├── services/
└── repositories/
tests/
```

Keep HTTP concerns in routes, business orchestration in services, and persistence in repositories. Inject external clients rather than constructing them inside route handlers. In tests, inject a fake model client so unit tests do not require network access or spend tokens.

Minimum tests:
1. missing required configuration fails clearly;
2. `/health` returns 200;
3. invalid request data returns 422;
4. model timeout maps to a safe, predictable API error;
5. fake model client is used and no real provider request occurs;
6. a repository failure is logged internally but does not expose a traceback or secret to the user.

Do not mark an async function as a performance optimization by itself. Async helps when the called I/O is genuinely non-blocking; CPU-heavy work and synchronous SDK calls need a different execution strategy.

## Day 43 — Cache correctness before speed

Implement cache-aside only for a read path with a clear freshness policy. For every cached object, specify:
- cache key namespace and schema version;
- tenant/user isolation dimension if data is private;
- TTL and why it is acceptable;
- invalidation event when the source changes;
- behavior when Redis is unavailable;
- metrics: hit, miss, error, and backend call count.

Test hit, miss, expiry, invalidation, Redis outage, and cross-user isolation. A cache hit must never bypass authorization. For LLM responses, include all material inputs in the cache key (model, prompt version, parameters, relevant context and access scope), or do not cache the response.

## Day 45–48 — Production quality progression

These days form one sequence rather than four unrelated topics:
- Day 45: request-level logs and traces explain **what happened to one operation**.
- Day 36: service metrics explain **how the whole service behaves over time**.
- Day 37: alerts turn selected metric conditions into **actionable intervention**.
- Day 46: cost telemetry explains **what each request and workload costs**.
- Day 47: security tests check **whether boundaries can be bypassed**.
- Day 48: evaluation harness checks **whether a change improves or regresses behavior**.

Keep correlation IDs in logs/traces, not metric labels. Keep secrets and raw private prompts out of all telemetry. A release decision should consider quality, reliability, security, latency, and cost together.
