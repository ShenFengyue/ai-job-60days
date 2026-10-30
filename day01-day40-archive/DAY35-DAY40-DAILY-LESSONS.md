# Day 35–Day 40 每日扩展学习记录

> 来源：2026-10-24 至 2026-10-29 当前对话中逐日生成的学习任务。以下整理保留各日主题、学习材料方向、编码练习、GitHub 交付物和验收要求；不代表用户已经完成这些任务。

## Day 35 — RAG API 可观测性：结构化日志与请求 ID
**日期：** 2026-10-24

### 学习目标
为每个 API 请求生成唯一 request_id；记录请求路径、HTTP 状态码、处理耗时；异常时保留可追踪日志；通过响应头将客户端请求与服务端日志关联。

### 学习材料
1. FastAPI 官方 Middleware 文档：理解 request、call_next、response，适合把请求 ID 与耗时统计放在统一中间件。
2. Python Logging Cookbook：学习 logger、日志级别、logger.exception() 与结构化字段。
3. OpenTelemetry Python 官方文档：了解 logs、metrics、traces 的区别；当天只实现基础日志。

### Coding Practice
在现有 FastAPI 项目增加请求日志中间件：
- UUID 生成 request_id，并保存到 request.state.request_id。
- 记录开始时间与耗时。
- 响应头返回 X-Request-ID。
- 记录 method、path、status_code、duration_ms。
- 异常时也要记录，并让原有异常处理继续工作。
- 不记录 API Key、隐私、完整 prompt 或敏感检索内容。

### GitHub Deliverable
新增或修改 middleware/request_logging.py、tests/test_request_logging.py、main.py、README.md。提交信息：`Day 35: add request logging and request IDs`。

### 验收
成功请求返回 request ID；失败请求有日志；日志字段齐全；测试覆盖成功、失败和日志检查；主动制造错误后能从日志定位对应请求。

### 求职
关注 AI 应用开发、LLM 应用、RAG/Agent 与 Python 后端岗位。面试题：为什么 request ID 有用？生产环境为什么不只用 print？求职动作：找 2 个岗位对照 JD，选最匹配的一个准备投递。

---

## Day 36 — Prometheus 指标监控
**日期：** 2026-10-25

### 学习目标
为 RAG API 增加请求量、错误量和请求延迟指标，理解 Counter、Histogram 与 /metrics 端点。

### 学习材料
1. Prometheus Python Client 官方 Instrumenting 文档：重点 Counter、Histogram。
2. Prometheus Histogram 官方文档：理解延迟分布与 P95，平均值不足以描述长尾。
3. OpenTelemetry Python 官方文档：了解统一可观测性体系，不要求当天接入全套工具。

### Coding Practice
安装 prometheus-client；实现：
- rag_requests_total：Counter，统计请求数。
- rag_request_errors_total：Counter，统计失败数。
- rag_request_duration_seconds：Histogram，统计耗时。
接入请求处理流程并暴露 /metrics。避免使用 request_id 或完整 URL 作为指标标签，防止高基数。

### GitHub Deliverable
新增或修改 monitoring/metrics.py、tests/test_metrics.py、main.py、requirements.txt、README.md。提交：`Day 36: add Prometheus metrics to RAG API`。

### 验收
成功请求增加计数；失败请求可统计；耗时进入 Histogram；/metrics 可读取；测试通过；README 有启动和验证说明。进行 10 次请求（至少 2 次失败）并核对指标。

### 求职
面试题：为什么关注 P95 而非只看平均值？Counter 与 Histogram 有何区别？求职动作：找 2 个岗位并完成一次正式投递或准备好可直接投递的简历。

---

## Day 37 — Prometheus 告警规则
**日期：** 2026-10-26

### 学习目标
根据指标定义错误率与 P95 延迟告警，理解 expr、for、labels、annotations，以及告警规则测试。

### 学习材料
1. Prometheus Alerting Rules 官方文档。
2. Prometheus Alerting 最佳实践：围绕用户可感知的问题告警，避免噪声。
3. Prometheus Unit Testing for Rules：使用 promtool test rules 验证触发条件。

### Coding Practice
创建 monitoring/alerts.yml，练习规则：
- 最近 5 分钟 HTTP 5xx 错误率超过 5%。
- 最近 5 分钟 P95 请求延迟超过 1.5 秒。
阈值仅为练习示例。表达式要与真实指标名、标签保持一致。使用 promtool check rules 和 promtool test rules 测试正常与超标场景。

### GitHub Deliverable
monitoring/alerts.yml、monitoring/alerts_test.yml、README.md。提交：`Day 37: add and test RAG API alert rules`。

### 验收
两类规则语法通过；测试覆盖正常与异常；能解释 rate()、histogram_quantile()、for；测试证明何时触发，而不只是 YAML 可解析。

### 求职
面试题：为什么看 P95？Prometheus 告警规则与 Alertmanager 分别负责什么？求职动作：找 2 个岗位并正式投递或修改针对性简历。

---

## Day 38 — Docker 容器化 RAG API
**日期：** 2026-10-27

### 学习目标
使用 Dockerfile 构建镜像并运行 RAG API，理解 image、container 与可复现运行环境。

### 学习材料
1. FastAPI 官方 Docker 部署教程。
2. Docker 官方 Python 应用容器化指南。
3. Docker 官方 Multi-stage builds 文档：了解构建阶段与运行阶段分离，当天不要求复杂实现。

### Coding Practice
为现有项目创建 Dockerfile 与 .dockerignore。基础示例使用 python:3.12-slim、WORKDIR、安装 requirements.txt、复制源代码，并以 uvicorn 在 0.0.0.0:8000 启动。按实际项目入口、Python 版本与数据文件调整。使用 docker build、docker run 验证 /docs、/health、已有的 /metrics 和真实 RAG 请求。不要把密钥写进镜像。

### GitHub Deliverable
Dockerfile、.dockerignore、README.md。提交：`Day 38: containerize RAG API with Docker`。

### 验收
镜像构建成功；容器可启动；外部可访问 API；健康检查与真实 RAG 请求正常；密钥未进入镜像或仓库；停止并重启后仍可运行。

### 求职
面试题：Docker 的价值是什么？为什么先复制 requirements.txt 再复制源代码？求职动作：找 2 个岗位，选择最匹配者投递或完成简历修改。

---

## Day 39 — Docker Compose
**日期：** 2026-10-28

### 学习目标
用 Compose 统一启动服务，掌握 build、ports、env_file、restart、healthcheck，区分容器启动与应用就绪。

### 学习材料
1. Docker Compose 服务配置参考。
2. Docker Compose 控制启动顺序指南：理解 healthcheck 与 service_healthy。
3. Docker Compose 环境变量管理指南：理解 env_file、environment 与 Secrets。

### Coding Practice
创建 compose.yaml，配置 API 构建、端口映射、.env、restart 和 /health 健康检查。创建 .env.example；确保 .env 在 .gitignore。运行 docker compose config --quiet、docker compose up --build -d、docker compose ps、curl /health、docker compose logs -f api、docker compose down。按实际项目端口、环境变量、数据持久化方式调整。

### GitHub Deliverable
Dockerfile、.dockerignore、compose.yaml、.env.example、.gitignore、README.md。提交：`Day 39: add Docker Compose deployment`。

### 验收
Compose 配置通过；服务启动且健康；RAG 核心接口可用；日志和停止命令可用；密钥不进仓库；重启后必要数据仍可用。

### 求职
面试题：Docker 与 Compose 区别？为什么容器运行不代表服务就绪？求职动作：找 2 个岗位并选择最匹配者投递或修改简历。

---

## Day 40 — GitHub Actions 自动构建与发布 Docker 镜像
**日期：** 2026-10-29

### 学习目标
使用 GitHub Actions 与 GitHub Container Registry 建立 CI/CD：提交代码后自动构建镜像，主分支提交通过后发布镜像。

### 学习材料
1. GitHub 官方 Publishing Docker images 文档。
2. Docker 官方 GitHub Actions 自动化构建指南。
3. docker/build-push-action 官方仓库：理解 Buildx、build-push-action、缓存与镜像标签。

### Coding Practice
创建 .github/workflows/publish-image.yml：
- Pull Request 触发构建检查，但不发布。
- 主分支 push 后登录 GHCR 并发布。
- 使用最小权限与 GITHUB_TOKEN。
- 镜像用 commit SHA 标记，避免只依赖 latest。
- 按实际默认分支名称调整触发条件。
验证 GitHub Actions 页面中的构建与发布结果。

### GitHub Deliverable
.github/workflows/publish-image.yml、README.md。提交：`Day 40: automate Docker image build and publish`。

### 验收
本地镜像构建成功；PR 能触发构建但不发布；主分支提交能发布 GHCR 镜像；标签对应代码提交；无硬编码密钥；README 说明流水线。

### 求职
面试题：为什么不能只使用 latest？为什么 PR 阶段只构建不发布？求职动作：找 2 个岗位并完成一次正式投递或针对性简历修改。简历中只描述真实完成并验证的功能。
