# 60-Day Curriculum

Start date: **2026-09-05 (Day 1)**

The goal is not to finish courses. The goal is to become able to independently ship AI applications and pass practical interviews.

## Day 01 — Python refresh
**Learn:** functions, dict/list, exceptions, modules, venv, pip, JSON.  
**Practice:** write `call_llm()` as a reusable Python function and save structured JSON output.  
**Deliverable:** `exercises/day01-python/` + one commit.  
**Materials:** Python tutorial — https://docs.python.org/3/tutorial/

## Day 02 — HTTP + APIs
**Learn:** HTTP methods, headers, JSON, environment variables, API keys.  
**Practice:** call an LLM API from Python with timeout and error handling.  
**Deliverable:** `exercises/day02-api/`.  
**Materials:** Requests — https://requests.readthedocs.io/en/latest/ ; OpenAI API docs — https://platform.openai.com/docs/

## Day 03 — Git and GitHub
**Learn:** commit, branch, diff, remote, README, `.gitignore`.  
**Practice:** turn Day 1–2 code into a clean Git repo with meaningful commits.  
**Deliverable:** first polished GitHub commit history.  
**Materials:** Git book — https://git-scm.com/book/en/v2

## Day 04 — LLM request/response anatomy
**Learn:** messages, system/user roles, tokens, context, temperature, model selection.  
**Practice:** build a CLI chat program with configurable model and system prompt.  
**Deliverable:** `exercises/day04-llm-cli/`.

## Day 05 — Prompt design
**Learn:** instructions, constraints, examples, decomposition, output contracts.  
**Practice:** create 10 prompt variants and compare outputs on the same test set.  
**Deliverable:** `notes/prompt-evaluation.md` + code.

## Day 06 — Structured output
**Learn:** JSON schemas, validation, retries, parsing failures.  
**Practice:** LLM returns a typed object for an English-word learning task.  
**Deliverable:** `exercises/day06-structured-output/`.  
**Materials:** Pydantic — https://docs.pydantic.dev/latest/

## Day 07 — Mini app
**Build:** English Learning Assistant: word → meaning, examples, mnemonic, related words.  
**Deliverable:** working local app + README + screenshot/GIF.  
**Acceptance:** another person can run it from the README.

## Day 08 — Embeddings
**Learn:** semantic similarity, embedding vectors, cosine similarity.  
**Practice:** embed 30 sentences and retrieve nearest neighbours.  
**Deliverable:** `exercises/day08-embeddings/`.  
**Materials:** Sentence Transformers — https://www.sbert.net/

## Day 09 — Vector search
**Learn:** vector indexing, top-k retrieval, metadata.  
**Practice:** build a tiny local vector search over your own notes.  
**Deliverable:** `exercises/day09-vector-search/`.

## Day 10 — Document ingestion
**Learn:** PDF/text extraction, cleaning, metadata.  
**Practice:** parse 3 PDFs and produce normalized chunks.  
**Deliverable:** ingestion script + sample output.

## Day 11 — Chunking
**Learn:** chunk size, overlap, semantic boundaries, metadata.  
**Practice:** compare three chunking strategies on one paper.  
**Deliverable:** `notes/chunking-experiment.md` + evaluation table.

## Day 12 — Retrieval
**Learn:** query transformation, top-k, filtering, retrieval failure modes.  
**Practice:** make a retriever return supporting passages for 20 questions.  
**Deliverable:** retrieval test set.

## Day 13 — First RAG
**Build:** PDF → chunks → embeddings → vector search → LLM answer.  
**Deliverable:** `projects/research-rag/` v0.

## Day 14 — RAG web app
**Build:** upload PDF, ask questions, show source passages.  
**Deliverable:** deployable ResearchAI v0.  
**Materials:** LlamaIndex RAG docs — https://docs.llamaindex.ai/

## Day 15 — Start applying
**Learn:** RAG pipeline end-to-end and how to explain it in interviews.  
**Practice:** draw your architecture from memory.  
**Deliverable:** `projects/research-rag/ARCHITECTURE.md`.  
**Job action:** 5–10 targeted applications.

## Day 16 — Retrieval evaluation
**Learn:** recall, precision, relevance, golden questions.  
**Practice:** create 30 retrieval test questions and score results.  
**Deliverable:** `evaluation/retrieval_eval.csv`.

## Day 17 — Metadata filtering
**Practice:** filter by document, page, date, topic.  
**Deliverable:** filter support + tests.

## Day 18 — Reranking
**Learn:** why initial retrieval and reranking are different.  
**Practice:** compare vector top-k with reranked top-k.  
**Deliverable:** benchmark note.

## Day 19 — Citation grounding
**Practice:** every answer must point to source chunks/pages. Reject unsupported claims.  
**Deliverable:** citation-aware answer pipeline.

## Day 20 — Conversation memory
**Learn:** short-term history vs persistent memory.  
**Practice:** follow-up questions that resolve references such as “this study”.  
**Deliverable:** memory implementation + test cases.

## Day 21 — Project 1 release
**Ship:** ResearchAI v1.0.  
**Deliverable:** public repo, demo, README, architecture, tests, limitations.

## Day 22 — Tool Calling
**Learn:** tool schema, arguments, tool result, validation.  
**Practice:** calculator + web/search + local database tools.  
**Deliverable:** `exercises/day22-tools/`.  
**Materials:** Hugging Face Agents Course — https://huggingface.co/learn/agents-course/en/unit1/introduction

## Day 23 — Agent loop
**Learn:** observe → decide → act → observe.  
**Practice:** implement a minimal loop without an agent framework.  
**Deliverable:** minimal agent in plain Python.

## Day 24 — Tool reliability
**Practice:** invalid args, timeouts, unavailable tools, retries.  
**Deliverable:** tool error-handling tests.

## Day 25 — Agent framework
**Learn:** use one framework after understanding the primitive.  
**Practice:** rebuild Day 23 agent with `smolagents` or LangGraph.  
**Deliverable:** framework version.  
**Materials:** https://huggingface.co/learn/agents-course/en/unit2 ; https://langchain-ai.github.io/langgraph/

## Day 26 — Research Agent
**Build:** question → search → retrieve → extract → synthesize.  
**Deliverable:** `projects/research-agent/` v0.

## Day 27 — Web + RAG tools
**Practice:** let the agent choose between web search and private documents.  
**Deliverable:** routing logic + tests.

## Day 28 — Agent memory/state
**Learn:** conversation state, task state, durable state.  
**Deliverable:** persistent agent state.

## Day 29 — Agent evaluation
**Practice:** 20 tasks with expected tool usage and expected outcomes.  
**Deliverable:** agent evaluation report.

## Day 30 — Project 2 release
**Ship:** Research Agent v1.0 with README, architecture, demo, evaluation.

## Day 31 — Backend foundations
**Learn:** REST, request validation, service boundaries.  
**Practice:** expose your LLM pipeline through FastAPI.  
**Materials:** https://fastapi.tiangolo.com/tutorial/

## Day 32 — Database
**Learn:** SQL, tables, indexes, CRUD.  
**Practice:** persist conversations and users.  
**Deliverable:** DB schema + migrations.

## Day 33 — Streaming
**Practice:** stream LLM output to the browser.  
**Deliverable:** streaming endpoint + UI.

## Day 34 — Authentication
**Practice:** simple login/session flow; never hard-code secrets.  
**Deliverable:** auth implementation + environment config.

## Day 35 — XiaoYa architecture
**Build:** separate UI, API, LLM, retrieval, memory and persistence.  
**Deliverable:** `projects/xiaoya-2/ARCHITECTURE.md`.

## Day 36 — XiaoYa retrieval
**Practice:** psychology knowledge base + cited retrieval.  
**Deliverable:** retrieval pipeline with evaluation set.

## Day 37 — XiaoYa tools
**Practice:** add safe utility tools and explicit tool policies.  
**Deliverable:** tool registry + tests.

## Day 38 — XiaoYa memory
**Practice:** persistent conversation history and user preferences.  
**Deliverable:** memory layer + tests.

## Day 39 — UX and failure states
**Practice:** empty state, timeout, no-source answer, retry, error UI.  
**Deliverable:** documented failure-state matrix.

## Day 40 — XiaoYa 2.0 release
**Ship:** deployed product, demo video, README, architecture, evaluation report.

## Day 41 — Docker
**Learn:** image, container, Dockerfile, compose.  
**Practice:** containerize one service.  
**Materials:** https://docs.docker.com/get-started/

## Day 42 — FastAPI production basics
**Learn:** settings, dependency injection, async endpoints, testing.  
**Practice:** production-style API layout.  
**Deliverable:** tests + settings module.

## Day 43 — Redis/cache
**Learn:** cache, session, TTL, rate limiting concepts.  
**Practice:** cache repeated retrieval/model calls where appropriate.

## Day 44 — Background jobs
**Learn:** queues and asynchronous work.  
**Practice:** move document ingestion to a background job.

## Day 45 — Logging/observability
**Practice:** structured logs for request, model, latency, token usage and tool errors.  
**Deliverable:** `notes/observability.md`.

## Day 46 — Cost engineering
**Learn:** token economics, model routing, caching, context trimming.  
**Practice:** estimate cost for 1k/10k/100k requests.  
**Deliverable:** cost model spreadsheet/markdown.

## Day 47 — Security
**Learn:** prompt injection, data leakage, secret handling, input validation.  
**Practice:** attack your own RAG and agent system.  
**Deliverable:** security test report.

## Day 48 — Evaluation harness
**Practice:** automate regression tests for prompts, retrieval and final answers.  
**Deliverable:** one-command evaluation script.

## Day 49 — Portfolio cleanup
**Practice:** remove dead code, add type hints, tests, setup instructions and screenshots.  
**Deliverable:** polished public GitHub repos.

## Day 50 — Portfolio release
**Ship:** final versions of ResearchAI, Research Agent and XiaoYa 2.0.

## Day 51 — Transformer fundamentals
**Learn:** tokens, embeddings, attention, transformer blocks, training vs inference.  
**Practice:** explain the architecture on paper without notes.

## Day 52 — RAG interview prep
**Practice:** answer top-k, chunking, reranking, hallucination, evaluation, latency and cost questions.  
**Deliverable:** `job-search/rag-interview.md`.

## Day 53 — Agent interview prep
**Practice:** tool calling, loops, state, memory, failure handling.  
**Deliverable:** `job-search/agent-interview.md`.

## Day 54 — Python interview prep
**Practice:** functions, OOP, iterators/generators, async, exceptions, data structures.  
**Deliverable:** 20 solved questions.

## Day 55 — System design
**Practice:** design an AI customer-support system and an AI research assistant.  
**Deliverable:** two architecture diagrams.

## Day 56 — Project storytelling
**Practice:** explain each project in 90 seconds, 5 minutes and 15 minutes.  
**Deliverable:** `job-search/project-stories.md`.

## Day 57 — Resume + portfolio
**Practice:** write impact-focused bullets around shipped software, evaluation and deployment.  
**Deliverable:** resume v1 + portfolio home.

## Day 58 — Interview simulation
**Practice:** one full technical mock interview and one project deep dive.  
**Deliverable:** gap list sorted by interview impact.

## Day 59 — Market feedback loop
**Practice:** review every rejection/interview question and map it to a missing skill.  
**Deliverable:** `job-search/feedback-log.md`.

## Day 60 — Employment readiness gate
**Must pass:**
- 3 working AI projects
- 2+ deployed demos
- clean public GitHub
- can explain RAG and Agents from first principles
- can debug API/deployment failures
- can build a new small AI application in 3–7 days
- active interview pipeline

**Decision:** stop preparing indefinitely. Continue learning through real job interviews and real product work.

## Primary learning sources

- Python: https://docs.python.org/3/tutorial/
- Git: https://git-scm.com/book/en/v2
- FastAPI: https://fastapi.tiangolo.com/tutorial/
- Docker: https://docs.docker.com/get-started/
- Hugging Face Agents Course: https://huggingface.co/learn/agents-course/en/unit1/introduction
- LlamaIndex: https://docs.llamaindex.ai/
- LangGraph: https://langchain-ai.github.io/langgraph/
- Pydantic: https://docs.pydantic.dev/latest/
- Sentence Transformers: https://www.sbert.net/

The daily automation should refresh these with current, high-value materials rather than replacing the project-driven curriculum with a course list.
