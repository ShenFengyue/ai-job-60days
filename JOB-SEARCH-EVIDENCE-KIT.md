# Job Search Evidence Kit — Lessons 49–60

The final phase is not a reading list. It is a collection of evidence that another person can inspect. A document existing in GitHub is not proof that the underlying skill or product works.

## Evidence levels

| Level | Evidence | What it proves |
|---|---|---|
| E0 | Notes or claims only | You have studied or planned the topic |
| E1 | Reproducible code + tests | You implemented a defined behavior |
| E2 | Working demo + test/evaluation report | The behavior works in a demonstrated environment |
| E3 | Real user, deployment, or interview feedback | The work has faced an external environment |

Use the lowest level that honestly describes the evidence. Never label E0 as PASS for an engineering capability.

## Day 49 — Portfolio cleanup evidence

For each project, record:

```markdown
## Project:
- Intended user and problem:
- Main user journey:
- Clean-environment setup tested on:
- Exact commands:
- Test command and result:
- Demo URL or local demo instructions:
- Architecture diagram:
- Known limitations:
- Security checks:
- Commit / release:
- What I personally implemented:
- What was AI-assisted or provided by a third party:
```

Run the setup from a fresh clone or clean environment. Record the OS, Python version, dependency installation command, and test result. Do not claim reproducibility if you only tested in your existing development environment.

## Day 50 — Release evidence

Use one record per repository:

| Field | Value |
|---|---|
| Repository | |
| Release tag / commit SHA | |
| Demo URL | |
| Clean install verified | PASS / PARTIAL / NOT YET |
| Core user path | |
| Automated tests | |
| Evaluation report | |
| Security scan | |
| Known limitations | |
| Rollback procedure | |

A tag is not a release gate. Only publish a stable version when the core path and documentation pass. Otherwise use a pre-release or keep the project explicitly in development.

## Day 51 — Transformer explanation rubric

Record a 3-minute explanation and score each item 0–2:
- tokenization and token IDs;
- embeddings and positional information;
- Q/K/V and attention weights;
- causal mask and next-token prediction;
- logits and decoding;
- training vs inference.

0 = incorrect/absent; 1 = broadly correct but vague; 2 = correct and connected to the generation process. Total score is a learning aid, not a formal certification. Link the recording or transcript and one runnable attention experiment.

## Day 52 — RAG interview evidence

Use at least 20 fixed questions if the project is ready; otherwise state the actual sample size. Record:

| Case ID | Expected evidence | Retrieved top-5 | Recall@5 | Answer correct? | Citation supported? | Latency | Failure stage |
|---|---|---|---:|---|---|---:|---|

Compare one controlled change at a time (for example dense vs hybrid retrieval). Keep the dataset version, model, prompt, retrieval parameters, and run date. Include three failure cases and the evidence that supports your diagnosis.

A strong answer explains the distinction:
- retrieval recall: was relevant evidence found?
- reranking: was useful evidence moved upward?
- generation faithfulness: are claims supported by context?
- citation validity: does each citation point to a real source that supports its claim?

## Day 53 — Agent interview evidence

Build a task set with normal and adversarial cases:

| Case | Expected tool | Argument constraints | Forbidden action | Expected outcome | Actual outcome |
|---|---|---|---|---|---|

Include invalid arguments, timeout, empty result, repeated call, permission denial, malformed model output, and side-effect confirmation. Save sanitized traces. Measure task success, tool selection/argument correctness, number of calls, latency, and cost. Verify side effects from external state; the model saying “done” is not proof.

## Day 54 — Python interview evidence

For each of the 20 exercises, keep:
- problem statement and assumptions;
- implementation;
- tests including one edge case;
- complexity where relevant;
- one-sentence explanation.

Suggested scoring: 0 = cannot implement; 1 = implementation works with hints or misses edge cases; 2 = independent implementation with tests and explanation. Re-do low-scoring questions after a delay instead of simply reading the solution.

## Day 55 — System design evidence

For each design, include:
1. functional and non-functional requirements;
2. explicit assumptions (traffic, concurrency, latency, data size);
3. API and data model;
4. architecture diagram with trust and sync/async boundaries;
5. one end-to-end request flow;
6. at least five failure modes and mitigations;
7. cost and capacity bottleneck;
8. what you deliberately did not build and why.

Do not invent scale numbers. Mark assumptions as assumptions and show how the design changes if they are wrong.

## Day 56 — Project storytelling evidence

Write three versions per project:
- 90 seconds: problem, user, outcome, your contribution, evidence.
- 5 minutes: architecture, key decision, implementation, evaluation, limitation.
- 15 minutes: failure analysis, alternatives, security, cost, scaling, what you would change.

Use this truth table:

| Claim | Evidence link | My contribution | AI/third-party contribution | Limitation |
|---|---|---|---|---|

Remove any claim without evidence or clearly label it as planned work.

## Day 57 — Resume and portfolio evidence

For every resume bullet, answer:
- What did I personally do?
- What problem did it solve?
- What artifact proves it?
- Is every number measured?
- Can I explain the implementation under questioning?

Use action + engineering method + result + evidence. If there is no measured result, describe the implemented capability without inventing a metric.

## Day 58 — Mock interview scorecard

| Question | Score (0–2) | Correct core idea | Missing evidence | Next drill |
|---|---:|---|---|---|

Score 0 = incorrect or no answer; 1 = definition-level; 2 = correct, project-grounded, and includes trade-offs. Record at least 10 questions. Choose the three gaps with the highest interview impact, not simply the questions you found hardest.

## Day 59 — Market feedback log

| Date | Role family | Stage | Exact feedback / question | Category | Repeated? | Evidence gap | Next action |
|---|---|---|---|---|---|---|---|

One rejection is weak evidence about a skill gap. Look for repeated patterns across multiple applications or interviews. Separate skill problems from role mismatch, experience level, location, compensation, and hiring-market constraints.

## Day 60 — Readiness gate

Mark each item PASS / PARTIAL / NOT YET and attach evidence:

| Capability | Status | Evidence | Next action |
|---|---|---|---|
| Python/API implementation | | | |
| Git workflow | | | |
| FastAPI/testing/configuration | | | |
| RAG retrieval + citations | | | |
| Agent tools + safety | | | |
| Docker/deployment | | | |
| Observability/debugging | | | |
| Evaluation/regression | | | |
| Portfolio demos | | | |
| Interview explanation | | | |
| Actual applications/feedback | | | |

A project can be useful even when it is not production-grade. The purpose of this gate is to make strengths and gaps visible, not to manufacture a pass.

## Final decision rule

Do not restart the 60 days because one checkbox is incomplete. Choose the next 30-day plan from the highest-impact evidence gaps and real market feedback. Keep one flagship project active; do not spread effort evenly across three projects if one already provides stronger proof of engineering ability.
