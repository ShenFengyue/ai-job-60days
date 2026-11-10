# Project Delivery Map

This map prevents the 60-day course from becoming 60 disconnected exercises. Not every day needs to modify a flagship project; standalone fundamentals are allowed. Every deliverable should have an explicit destination and purpose.

## Three flagship projects

| Project | Role in portfolio | Main proof |
|---|---|---|
| ResearchAI | Primary RAG application | Document ingestion, retrieval quality, citations, evaluation |
| Research Agent | Agent/workflow application | Tool execution, state, task completion, safety, trace evaluation |
| XiaoYa 2.0 | Product-oriented AI application | User experience, memory, persistence, permissions, deployment |

## Delivery mapping

| Days | Primary destination | Expected output |
|---|---|---|
| 01–07 | Standalone exercises → English Learning Assistant | Python/API/LLM fundamentals and one small working app |
| 08–15 | ResearchAI | Embeddings, vector search, ingestion, chunking, retrieval, first RAG demo |
| 16–20 | Research Agent + ResearchAI | Tool calling fundamentals; retrieval/citation/memory integration |
| 21 | ResearchAI | Release evidence and architecture |
| 22–30 | Research Agent | Tool schemas, agent loop, reliability, framework comparison, evaluation, release |
| 31–34 | Shared backend foundation | FastAPI, database, streaming, authentication patterns |
| 35–40 | XiaoYa 2.0 | Product architecture, retrieval/tools/memory/UX, release |
| 41–48 | Shared production-lab → relevant project | Security, configuration, caching, background jobs, observability, cost, evaluation |
| 49–50 | All three, but prioritize strongest | Portfolio cleanup and release; do not fake completion |
| 51 | Standalone fundamentals | Transformer explanation and attention experiment |
| 52 | ResearchAI | RAG interview answers backed by evaluation data |
| 53 | Research Agent | Agent interview answers backed by traces and task tests |
| 54 | Job-search artifact | Solved Python interview exercises |
| 55 | Job-search artifact | Two system-design case studies |
| 56 | All three | Evidence-backed project stories |
| 57 | Job-search artifact | Resume and portfolio landing page |
| 58 | Job-search artifact | Mock interview scorecard |
| 59 | Job-search artifact | Market feedback log and next-30-day plan |
| 60 | Job-search artifact | Readiness gate with evidence links |

## How to decide where a feature belongs

1. If it proves a language or library primitive, keep it in `exercises/`.
2. If it improves document ingestion, retrieval, citations, or RAG quality, put it in ResearchAI.
3. If it improves tool selection, task state, execution, or agent reliability, put it in Research Agent.
4. If it improves a real user journey, persistent preferences, permissions, or product behavior, put it in XiaoYa 2.0.
5. If it demonstrates interview readiness or market learning, put it in `job-search/`.

Avoid copying an entire exercise into all three products. Port only the reusable capability that the project actually needs.

## Definition of done for a project feature

- [ ] User problem and expected behavior are stated.
- [ ] Implementation is linked from the project README.
- [ ] At least one happy-path test exists.
- [ ] At least one failure/edge case is tested.
- [ ] Secrets and private data are not committed.
- [ ] Evaluation evidence is recorded when quality is probabilistic.
- [ ] Known limitations are stated.
- [ ] A commit or release reference is recorded.

A lesson deliverable may be complete while the corresponding portfolio feature is still PARTIAL. Keep those statuses separate.
