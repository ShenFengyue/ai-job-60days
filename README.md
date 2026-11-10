# AI Job 60 Days

> 60-day sprint: from existing Python/LLM application experience to AI job readiness.

## Objective

Build and ship 3 AI applications, publish real engineering work on GitHub, deploy demos, start applying from Day 15, and use interview feedback to drive learning.

## Strategy

**Build first. Learn only what the build requires. Apply early.**

This is intentionally an AI application / LLM engineering track rather than a model-training track.

### Core stack

`Python` · `LLM APIs` · `Structured Output` · `Embeddings` · `RAG` · `Vector DB` · `Tool Calling` · `Agents` · `FastAPI` · `SQL` · `Docker` · `Deployment` · `Evaluation`

## 60-day structure

| Days | Focus | Output |
|---|---|---|
| 1–7 | Python, Git, HTTP/API、LLM 基础与第一个小应用 | 可运行的 English Learning Assistant |
| 8–15 | Embedding、向量检索、Chunking、RAG 与第一个部署项目 | ResearchAI / Mini RAG |
| 16–23 | Tool Calling、Agent Loop、Agentic RAG、评估、追踪与成本意识 | 最小 Research Agent 与评估记录 |
| 24–31 | FastAPI、Docker、CI、Web/RAG 工具、Hybrid Search、Agent 评估 | 可调用、可部署、可测试的 Agent 服务 |
| 32–40 | 数据库、Streaming、可靠性、可观测性、容器与发布 | 产品化后端与 CI/CD 流水线 |
| 41–50 | 安全、生产配置、缓存、后台任务、成本、评估与作品集发布 | 经过安全/质量检查的项目作品集 |
| 51–60 | Transformer 基础、技术面试、系统设计、简历与求职反馈 | 面试证据与 30 天行动计划 |

## Daily learning materials

The daily automation is configured separately to collect fresh, high-quality materials and practice tasks. It prioritizes official documentation and current primary sources, and avoids link-dumping.

The repository stores the stable curriculum; daily research can adapt to current tools and docs.

## Portfolio projects

### 1. ResearchAI — Academic RAG

PDF → parsing → chunking → embeddings → vector search → reranking → cited answers.

### 2. Research Agent

LLM + tools + retrieval + memory + web search + task execution.

### 3. XiaoYa 2.0

A production-oriented AI psychology assistant with memory, retrieval, tools, persistence, evaluation, and deployment.

## Repository workflow

Every study day:

1. Read only the day's core material.
2. Complete the coding practice.
3. Apply it to the current project.
4. Commit the result.
5. Record one thing learned and one thing that broke.
6. From Day 15 onward, do a concrete job-search action.

## Course files and how to use them

- [Daily lessons (canonical)](Lessons/): the actual day-by-day teaching materials. Follow `Lessons/01.md` through `Lessons/60.md` in order; this folder is the source of truth for daily execution.
- [60-day curriculum blueprint](CURRICULUM.md): the original high-level learning design. It may not reflect every change made to the live daily lessons; when day-level topics differ, follow `Lessons/`.
- [Daily study workbook](curriculum/ALL-DAYS.md): supplementary workbook and historical planning material; do not use it to override the canonical daily lessons.
- [Progress tracker](PROGRESS.md): current date mapping and completion evidence. The active reset is **2026-10-05 = Day 16**; do not use the old date mapping.
- [Learning method](LEARNING-METHOD.md): daily learn-build-test-commit loop.
- [Git for beginners](GIT-FOR-BEGINNERS.md): repository workflow for learners new to Git.
- [Job search](JOB-SEARCH.md): target roles, application workflow, portfolio evidence, and interview topics.
- [Day 01–40 archive](day01-day40-archive/README.md): historical daily lessons and corrected Day 16–40 date mapping.
- [Portfolio project index](projects/README.md): the three intended flagship projects.

The curriculum/day-*.md files are retained as expanded lesson notes for selected days; they are not disposable duplicates of the shorter daily workbook. The archive contains unique expanded Day 35–40 lessons and is also retained.

## Interview target

Target roles include AI Application Engineer, LLM Engineer, AI Agent Engineer, AI Product Engineer, AI Developer, AI Solutions Engineer, and technical AI product roles.
