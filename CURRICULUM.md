# 60-Day Curriculum — Canonical Index

**Current daily source of truth:** [Lessons/01.md–Lessons/60.md](Lessons/)

The detailed daily topics, explanations, exercises, and acceptance criteria live in the numbered lesson files. This document is the stable map of the learning route; it intentionally does not duplicate the daily teaching material.

## Goal

Build the ability to independently design, implement, test, deploy, evaluate, and explain AI applications. This is an **AI application / LLM engineering** route, not a model-training research curriculum.

## Current date mapping

The active reset is **2026-10-05 = Day 16**. Therefore:
- Day 01 = 2026-09-20
- Day 16 = 2026-10-05
- Day 60 = 2026-11-18

See [PROGRESS.md](PROGRESS.md). A day is not complete merely because its date has passed; completion requires learner evidence.

## Course phases

| Days | Phase | Main capabilities | Main destination |
|---|---|---|---|
| 01–07 | Programming and first LLM app | Python, Git, HTTP/API, LLM request/response, prompting, structured output | Standalone exercises → English Learning Assistant |
| 08–15 | RAG foundations | Embeddings, vector search, ingestion, chunking, retrieval, reranking, first RAG product | ResearchAI |
| 16–23 | Tool use and agent foundations | Tool schemas, execution boundary, agent loop, state/memory, retrieval and tool integration | Research Agent + ResearchAI |
| 24–31 | Agent engineering and backend | Failure handling, frameworks, agent evaluation, FastAPI service, API boundaries | Research Agent |
| 32–40 | Product and delivery engineering | Persistence, streaming, authentication, product architecture, UX/failure states, Docker, Compose, CI | XiaoYa 2.0 + shared backend |
| 41–48 | Production quality | Security scanning, configuration, cache, background jobs, observability, cost, security, evaluation harness | Shared production lab → relevant flagship project |
| 49–50 | Portfolio release | Reproducibility, cleanup, release gates, real demos and limitations | All three projects; prioritize strongest evidence |
| 51–60 | Interview and employment readiness | Transformer fundamentals, RAG/Agent/Python interviews, system design, project storytelling, resume, mock interview, market feedback | `job-search/` |

## Three flagship projects

1. **ResearchAI** — document ingestion, RAG, retrieval quality, reranking, citations, and evaluation.
2. **Research Agent** — tool selection and execution, state, task completion, reliability, and safety.
3. **XiaoYa 2.0** — product experience, memory, persistence, permissions, and deployment.

See [PROJECT-DELIVERY-MAP.md](PROJECT-DELIVERY-MAP.md) for the day-by-day destination of deliverables and the definition of done.

## How to use the course

1. Read the canonical lesson for the day.
2. Complete the smallest runnable exercise before adding optional complexity.
3. Test one normal path and at least one failure/edge case.
4. Port the capability into the mapped flagship project only when it genuinely belongs there.
5. Commit code, test output, and a short explanation.
6. From the job-search phase onward, attach evidence to every claim.

The production lessons share a consistent local target and are supported by [COURSE-IMPLEMENTATION-GUIDE.md](COURSE-IMPLEMENTATION-GUIDE.md). The final phase uses [JOB-SEARCH-EVIDENCE-KIT.md](JOB-SEARCH-EVIDENCE-KIT.md).

## Historical material

Older planning documents that duplicated or conflicted with the live daily lessons have been removed. The numbered `Lessons/` files are the single source of truth.

## Quality boundary

This curriculum index and its companion guides define intended work. They do **not** prove that every sample has been executed on the learner's machine, that every external link remains available, or that the three portfolio projects are already implemented/deployed. Record those facts separately in [PROGRESS.md](PROGRESS.md) and the project evidence.
