# AI Job 60 Days — Course Audit and Revision Record

**Revision date:** 2026-11-11  
**Scope:** Static review and repository edits covering `Lessons/01.md`–`Lessons/60.md`, README, curriculum index, progress tracker, and supporting course guides.

## Executive result

The course has been revised to address the major content-structure issues found in the previous audit:

- The 60 numbered lesson files remain the canonical daily source.
- The stale detailed curriculum has been preserved as historical material; `CURRICULUM.md` is now a current high-level index aligned with the live course.
- A project delivery map assigns lesson outputs to ResearchAI, Research Agent, XiaoYa 2.0, standalone exercises, or job-search artifacts.
- A topic progression map explains why recurring topics reappear and what new capability each pass adds.
- Production lessons now share a consistent local FastAPI lab path for metrics, alerts, containers, Compose, CI, security, API structure, caching, and production-quality integration.
- Days 49–60 now link to explicit evidence templates and scoring rubrics.
- Lesson-level progression/evidence notes were added to Days 36–43, 45–60.

## Repository changes made in this revision

### New documents

1. `COURSE-IMPLEMENTATION-GUIDE.md` — one consistent FastAPI target and reproducible local procedures for Days 36–48.
2. `JOB-SEARCH-EVIDENCE-KIT.md` — concrete templates, scoring rubrics, and evidence rules for Days 49–60.
3. `PROJECT-DELIVERY-MAP.md` — maps each phase to the three flagship projects and defines feature-level completion.
4. `TOPIC-PROGRESSION.md` — distinguishes first principles, integration, production measurement, and interview evidence for recurring topics.
5. `CURRICULUM-ORIGINAL-BLUEPRINT.md` — preserves the former detailed blueprint for historical reference.

### Updated documents

- `CURRICULUM.md` — replaced the stale daily sequence with a canonical phase index and current date mapping.
- `README.md` — links all guides and states that written notes are not proof of working functionality.
- `Lessons/36.md`–`Lessons/43.md`, `Lessons/45.md`–`Lessons/60.md` — added progression or evidence links to the companion guides.

Earlier corrections remain in place:
- Day 44 is Background Jobs, not a duplicate of Day 46.
- Day 2 uses the current DeepSeek model identifier `deepseek-flash` in the sample.
- README identifies `Lessons/` as the canonical daily course.

## Problems addressed

### 1. Uneven teaching depth and reproducibility

The production engineering guide now gives a consistent runnable target, a working FastAPI metrics example, Prometheus scrape configuration, alert-rule validation, Docker/Compose assumptions, CI security boundaries, test requirements, and cache correctness checks.

This does not mean every lesson is now a full textbook chapter. The guide is a shared implementation companion to reduce repeated boilerplate and keep the daily lessons focused.

### 2. Repeated topics without clear progression

The new progression map clarifies:
- reranking: Day 13 fundamentals → Day 29 integrated use/evaluation → Day 52 interview evidence;
- tool calling/agents: Day 16 primitive → later loop/state/reliability integration → Day 53 interview evidence;
- observability: single trace → service integration → metrics/alerts → cross-request investigation;
- cost: early awareness → unit economics → evaluation of quality/cost trade-offs;
- evaluation: retrieval set → agent tasks → regression harness → readiness evidence.

### 3. Weak project linkage

The project delivery map assigns each phase to a clear destination. Standalone exercises remain standalone unless there is a genuine reason to port them. This avoids copying every tutorial into all three portfolio projects.

### 4. Final-phase claims not backed by evidence

The evidence kit requires code, tests, demos, sanitized traces, measured results, recordings/transcripts, application records, or feedback as appropriate. It distinguishes notes from working implementation and external validation.

### 5. Curriculum and lesson sequence inconsistency

The old detailed curriculum is preserved in `CURRICULUM-ORIGINAL-BLUEPRINT.md`. The new `CURRICULUM.md` is a navigational index and no longer pretends that the old Day 16–50 schedule matches the current lesson files.

## Remaining verification boundaries

This revision is a **static repository and instructional-design improvement**, not a claim of end-to-end execution.

Still not verified in this pass:
- Every Python example on Windows, macOS, and Linux.
- Every YAML workflow against a live GitHub Actions run.
- Every Docker/Compose stack against a clean machine.
- Every external URL and third-party action at the time a learner runs it.
- Whether ResearchAI, Research Agent, and XiaoYa 2.0 currently satisfy their lesson deliverables.
- Whether any learner has completed the work or achieved job readiness.

The FastAPI example in the implementation guide is a teaching target. Its deliberate blocking route is there to demonstrate a failure mode; remove it from real async applications. Prometheus metric behavior, multi-worker configuration, and alert thresholds must be validated for the actual deployment. Image tags and third-party Actions must be pinned/verified for production security.

## Recommended next verification pass

1. Clone the repository into a clean environment and run the production-lab steps in order.
2. Run syntax checks and tests for every Python/YAML sample; fix examples that fail rather than marking them as complete.
3. Add CI that validates Markdown links, Python formatting/tests, and workflow YAML.
4. Verify the three flagship projects from clean install instructions and attach real test/demo evidence.
5. Review external links and mutable model/action versions immediately before each daily lesson is used.

## Completion rule

Do not change `PROGRESS.md` to PASS based on repository edits performed by the assistant. The learner's implementation and evidence are required. The goal is a course that can guide and assess real engineering work—not a repository that merely looks complete.
