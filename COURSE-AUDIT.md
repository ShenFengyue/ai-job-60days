# AI Job 60 Days — Course Audit

**Audit date:** 2026-11-11  
**Scope:** Static review of `Lessons/01.md`–`Lessons/60.md`, `README.md`, `CURRICULUM.md`, and `PROGRESS.md`. This is a content and consistency review; it does not claim that every code sample has been executed or every external link has been tested end-to-end.

## Executive result

- All 60 numbered lesson files exist and are non-empty.
- The actual dated lesson sequence is now explicitly designated as `Lessons/` in the README.
- Day 44 was a duplicate of Day 46 and has been replaced with the intended Background Jobs lesson.
- Day 2 now uses the current official DeepSeek model identifier `deepseek-flash`.
- The README's phase table now describes the actual lesson sequence rather than the older blueprint.

## Corrections made in this audit

### 1. Day 44 duplicate removed

The former `Lessons/44.md` was a copy of the Day 46 cost-engineering lesson, including the November 4 / Day 46 date. It has been replaced with **Background Jobs** (November 2 / Day 44), matching the original curriculum intent.

The replacement teaches:
- synchronous request vs FastAPI BackgroundTasks vs independent Worker/Queue;
- task IDs and lifecycle states;
- retries, idempotency, timeouts, dead-letter handling;
- a deliberately limited in-memory teaching example;
- why durable work needs persistent task state and an independent worker.

### 2. Daily source of truth clarified

The README now states that `Lessons/01.md`–`Lessons/60.md` are the canonical day-by-day materials. `CURRICULUM.md` is the original curriculum blueprint; where it differs from the live lesson sequence, follow `Lessons/`. This avoids silently pretending the two schedules are identical.

### 3. README phase map corrected

The phase table now reflects the actual progression: foundations; RAG; tools and agents; API/deployment/retrieval engineering; product/production engineering; and interview/job-search preparation.

### 4. Day 2 model identifier corrected

The sample now uses `deepseek-flash`. The former `deepseek-v4-flash` identifier is retained by the provider only for compatibility with a retired model generation; new examples should use the current identifier.

## Findings that remain for a deeper revision

### A. Lesson depth is uneven

The early lessons (especially Days 1–15 and several of Days 16–31) tend to include fuller explanations, implementation steps, experiments, deliverables, and acceptance criteria. A number of later lessons (particularly Days 36–43 and 49–60) are much shorter. They are useful as guided task sheets, but not all of them yet function as standalone beginner-friendly textbook chapters.

**Recommended fix:** Expand the short lessons with one worked example, explanation of each important code block, common failure cases, a test procedure, and a concrete acceptance check. Do not add length by adding more links or jargon.

### B. Repeated themes need explicit progression

Some subjects appear more than once:
- Tool calling / agent execution: Days 16–20 and again Days 30–31.
- Reranking: Day 13 and Day 29.
- Observability: Days 21, 31, 35–37 and 45.
- Cost/performance: Day 22 and Day 46.

These repetitions can be useful if each pass has a different level. The lessons should explicitly state the progression:
- first principles → framework/project implementation → production measurement;
- basic dense reranking → hybrid retrieval plus reranking;
- application traces → service metrics/alerts → cross-system cost and failure analysis;
- performance baseline → provider pricing and unit economics.

**Recommended fix:** Add a short “How this builds on earlier days” paragraph to each repeated-topic lesson and avoid re-teaching the same introductory definition.

### C. Some lessons need a stronger runnable path

The later production lessons describe important concepts but often stop before a complete local exercise. Prioritize:
- Days 36–37: a minimal Prometheus scrape target, sample metrics, and a rule test;
- Days 38–40: a working Docker/Compose/Actions path with explicit assumptions;
- Days 41, 45, 47–48: reproducible security, observability, and evaluation tests;
- Days 52–60: answer rubrics and evidence templates that can be used in an actual interview/job search.

### D. Project milestones should be tied together

The repository describes three flagship projects, but individual lessons sometimes ask for generic exercises without clearly saying which project receives the result.

**Recommended fix:** Each lesson should label its output as one of:
1. a standalone exercise;
2. a feature added to ResearchAI;
3. a feature added to Research Agent;
4. a feature added to XiaoYa 2.0;
5. a job-search artifact.

The README should point to the exact project folder for each milestone.

### E. Final ten days should be evidence-driven

The interview and job-search lessons have useful prompts and checklists, but should avoid implying that reading or writing a preparation note proves competence. Each PASS should link to a real code artifact, test, demo, recorded explanation, or actual application/interview result.

## Technical freshness checked during this audit

- Day 2 now uses the provider's current `deepseek-flash` model ID.
- Day 46's displayed per-million-token price table matches the official DeepSeek pricing page checked on 2026-11-11. Pricing is mutable; always re-check the linked official page before using it for a real cost forecast.
- Day 40 uses current major Docker Action lines in its example. Check the action release pages before copying into a production workflow, and pin verified commit SHAs where supply-chain assurance requires it.

## What this audit does not claim

- It does not prove every Python/YAML command works in every operating system.
- It does not prove that every external resource URL remains available.
- It does not verify that the three portfolio applications are implemented or deployed.
- It does not mark any day complete in `PROGRESS.md`; progress requires evidence from the learner.

## Recommended revision order

1. Expand Days 36–43 into reproducible beginner-level labs.
2. Expand Days 49 and 52–60 with concrete evidence templates and worked answers.
3. Add explicit progression notes to repeated themes.
4. Link every deliverable to one of the three actual project directories.
5. Run the code examples in a clean environment and record the tested Python/package versions.
