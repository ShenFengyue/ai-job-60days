# Topic Progression Map

Repeated topics are intentional only when each revisit adds a new capability. Use this map to avoid restarting from definitions every time a concept appears.

| Topic | First pass | Build / integration pass | Production / evidence pass | What changes between passes |
|---|---|---|---|---|
| Reranking | Day 13 | Day 29 | Day 52 | Day 13 learns dense retrieval + cross-encoder ordering; Day 29 applies ranking inside the agent/retrieval workflow and evaluates the combined pipeline; Day 52 explains ranking trade-offs with real ResearchAI measurements. |
| Tool calling and agents | Day 16 | Days 22–30 | Day 53 | Day 16 learns schema → model proposal → host validation/execution; later days add loops, state, failures, framework integration, and task evaluation; Day 53 turns those decisions into interview evidence. |
| Memory and state | Day 20 | Day 28 and XiaoYa work | Day 53 / Day 55 | Day 20 distinguishes conversation context from persistent memory; Day 28 handles durable task state; product work adds user-facing persistence and permissions; interview/system design tests lifecycle and privacy. |
| Observability | Day 21 | Days 31 and 35 | Days 36–37 and 45 | Start with one execution trace; integrate service-level request context; add metrics and alert rules; use structured logs/traces to investigate one request. Keep high-cardinality identifiers in logs/traces, not metric labels. |
| Cost and performance | Day 22 | Day 46 | Days 48, 52–53 | Early awareness of token/context costs; explicit unit-economics calculator and model-routing trade-offs; regression/evaluation measures whether cost optimization damages answer quality or agent success. |
| Evaluation | Days 12–15 | Days 29 and 48 | Days 52–60 | Small retrieval test set → agent task tests → unified regression harness → interview evidence and readiness decisions. A mock-only harness is not proof of a live application passing. |
| Reliability and security | Days 24–25 | Days 37–43 and 47 | Days 50, 55, 60 | Tool-level timeout/retry → service monitoring, cache/queue behavior, security boundaries → release gates and system-design reasoning. |

## Rules for revisiting a topic

1. Do not repeat the introductory definition unless the earlier lesson was not completed.
2. State the new engineering question this pass answers.
3. Reuse the previous day's code/data when possible.
4. Change one major variable per experiment.
5. Preserve a before/after measurement or failure case.
6. State what this pass does **not** prove.

A repeated topic without a higher-level implementation, measurement, or decision is redundant content and should be removed or replaced.
