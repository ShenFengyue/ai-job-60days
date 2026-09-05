# AI Job 60 Days — Daily Study Workbook

> Start: 2026-09-05. 每一天都按“学懂 → 动手 → 产出 → Git 提交 → 验收”执行。
> 建议每天 6–8 小时：学习 2h、编码 3h、项目 2h、求职 1h（Day 15 起）。

## Day 01 — Python refresh + first AI script
**目标**：能独立创建 Python 项目、运行脚本、安装依赖、处理 dict/list/function/exception/JSON，并理解 AI API 的基本调用方式。
**学习**：Python 教程 https://docs.python.org/3/tutorial/；虚拟环境、pip、JSON、异常处理。
**实践**：创建 `exercises/day01-python/main.py`，实现 `call_llm(prompt)`；输入一句话，返回文本，并保存成 JSON。
**产出**：`requirements.txt`、`.env.example`、README、可运行代码。
**验收**：能解释函数、dict、异常、venv、JSON；能从终端运行程序。
**Git**：`git status` → `git add .` → `git commit -m "Day 01: Python and first AI call"` → `git push`。

## Day 02 — HTTP + APIs
**目标**：理解 HTTP、URL、headers、status code、JSON、API key、timeout。
**学习**：Requests Quickstart https://requests.readthedocs.io/en/latest/user/quickstart/；MDN HTTP https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview；模型供应商 API 文档。
**实践**：Python 调 LLM API，加入 timeout、异常处理、错误信息；API key 从环境变量读取。
**产出**：`exercises/day02-api/` + README + `.env.example`。
**验收**：能解释 200/400/401/429/500；知道为什么 API key 不能上传 GitHub。
**Git**：提交一次有意义的 commit。

## Day 03 — Git and GitHub from zero
**目标**：真正会用 Git。
**学习**：Git Book https://git-scm.com/book/en/v2；GitHub Git basics https://docs.github.com/en/get-started/learning-to-code/getting-started-with-git。
**实践**：clone 本仓库；新建文件；`status`、`diff`、`add`、`commit`、`log`、`push`、`pull` 全部实际使用一遍。
**产出**：`exercises/day03-git/README.md`，记录命令和你自己的解释。
**验收**：能说清 working tree → staging → commit → remote。
**Git**：今天不追求漂亮历史，只追求会用。

## Day 04 — LLM request/response anatomy
**目标**：理解 system/user/assistant、token、context window、temperature、model。
**学习**：OpenAI API docs https://platform.openai.com/docs/；Hugging Face LLM Course https://huggingface.co/learn/llm-course/。
**实践**：写 CLI Chat；固定 system prompt；连续 5 轮；模型从环境变量读取。
**产出**：`exercises/day04-llm-cli/`。
**验收**：能画出 user → API → model → response；解释上下文为何影响成本和长度。

## Day 05 — Prompt design
**目标**：从“会问 AI”升级为“会设计模型任务”。
**学习**：instructions、constraints、examples、decomposition、output contract。
**实践**：选 10 个英文学习任务，写 10 个 prompt 版本；固定测试集，比较准确性、格式稳定性、长度。
**产出**：`notes/prompt-evaluation.md` + `exercises/day05-prompt/`。
**验收**：知道什么时候使用示例、约束、分步任务；不把 prompt 当魔法咒语。

## Day 06 — Structured output
**目标**：让 LLM 输出程序能直接消费的数据。
**学习**：JSON Schema、Pydantic https://docs.pydantic.dev/latest/、校验与重试。
**实践**：英文单词输入 → `meaning/examples/mnemonic/related_words` 的结构化对象；格式错误时自动重试或报错。
**产出**：`exercises/day06-structured-output/`。
**验收**：能说明自然语言输出和结构化输出的区别。

## Day 07 — Mini App: English Learning Assistant
**目标**：第一次完成一个闭环 AI 应用。
**实践**：输入单词 → LLM → 释义/例句/记忆法/相关词；做最小 Web 或 CLI UI。
**产出**：`projects/english-assistant/`，README、截图、运行说明。
**验收**：别人只看 README 就能运行；代码中没有 API key。

## Day 08 — Embeddings
**目标**：理解语义向量，不背数学公式。
**学习**：Sentence Transformers https://www.sbert.net/。
**实践**：准备 30 句话，生成 embedding；计算相似度；找每句话最近的 3 个邻居。
**产出**：`exercises/day08-embeddings/` + 实验笔记。
**验收**：能解释“文字 → 向量 → 相似度”。

## Day 09 — Vector search
**目标**：把 embedding 变成可检索的数据结构。
**学习**：FAISS/Chroma/pgvector 三选一；理解 index、top-k、metadata。
**实践**：对个人学习笔记做本地向量搜索；输入问题返回 top-5 passages。
**产出**：`exercises/day09-vector-search/`。
**验收**：解释 top-k 为什么不是越大越好。

## Day 10 — Document ingestion
**目标**：理解 RAG 的“数据入口”。
**学习**：PDF/text parsing、cleaning、metadata。
**实践**：解析 3 篇 PDF；输出统一的 `{text, source, page, title}` 结构。
**产出**：`exercises/day10-ingestion/`。
**验收**：能解释为什么原始 PDF 不能直接喂给向量库。

## Day 11 — Chunking
**目标**：理解切块是 RAG 质量的关键变量。
**实践**：对同一论文测试 300/500/1000 token 三种 chunk；比较检索结果。
**产出**：`notes/chunking-experiment.md` + 结果表。
**验收**：能说出 chunk size、overlap、semantic boundary 各自的作用。

## Day 12 — Retrieval
**目标**：让系统真正找到支持答案的原文。
**学习**：top-k、metadata filtering、query transformation、retrieval failure。
**实践**：写 20 个问题；每题输出 top-5 passages；人工标记是否包含答案依据。
**产出**：`evaluation/retrieval-test-set.json`。
**验收**：能区分“检索错”和“模型说错”。

## Day 13 — First RAG
**目标**：完成第一条完整 RAG pipeline。
**流程**：PDF → parse → chunk → embedding → vector DB → retrieval → LLM。
**实践**：选择 5 篇你熟悉的心理学论文；支持问答。
**产出**：`projects/research-rag/` v0。
**验收**：回答必须能够追溯到文档片段。

## Day 14 — RAG Web App
**目标**：从脚本变成可使用产品。
**实践**：上传 PDF、提问、显示答案和来源页；加入 loading/error 状态。
**学习**：LlamaIndex RAG docs https://docs.llamaindex.ai/ 或自己用原生 Python 实现。
**产出**：ResearchAI v0，在线或本地 Demo。
**验收**：新用户 3 分钟内能完成第一次问答。

## Day 15 — Start applying
**目标**：开始让市场验证学习方向。
**实践**：从记忆画出 RAG 架构；写 5 分钟项目介绍。
**求职**：投 5–10 个 AI Application / LLM / Agent / AI Product 技术岗位。
**产出**：`projects/research-rag/ARCHITECTURE.md` + 第一批投递记录。
**验收**：能回答“为什么 RAG 而不是直接 Prompt？”

## Day 16 — Retrieval evaluation
**目标**：从“感觉效果不错”转向可测量。
**学习**：recall、precision、relevance、golden set。
**实践**：30 个问题，人工标注正确 supporting chunk；统计 recall@k。
**产出**：`evaluation/retrieval_eval.csv` + `notes/eval.md`。
**求职**：继续 5–10 投递。

## Day 17 — Metadata filtering
**目标**：让检索利用 source/page/date/topic 等结构化信息。
**实践**：支持按论文、年份、主题过滤；设计 10 个过滤测试。
**产出**：过滤代码 + 单元测试。
**验收**：解释为什么 metadata filtering 可以减少检索噪音。

## Day 18 — Reranking
**目标**：理解 first-stage retrieval 和 reranking 的区别。
**学习**：cross-encoder/reranker 基本思想。
**实践**：同一个问题比较 vector top-10 与 reranked top-5；记录变化。
**产出**：`notes/rerank-benchmark.md`。
**验收**：能说清 reranker 为什么比单纯 cosine similarity 更精细。

## Day 19 — Citation grounding
**目标**：让模型不能“无来源发挥”。
**实践**：答案中的每条关键陈述必须映射到 source chunk/page；无依据则回复“资料不足”。
**产出**：citation-aware pipeline + 10 个失败测试。
**验收**：能解释 hallucination 与 retrieval grounding 的关系。

## Day 20 — Conversation memory
**目标**：处理多轮对话中的指代。
**学习**：短期 history、摘要记忆、持久化 memory。
**实践**：支持“这项研究”“刚才那个方法”等 follow-up；写 10 个测试。
**产出**：memory layer + test cases。
**验收**：知道 context history 和 database memory 不是一回事。

## Day 21 — ResearchAI v1.0
**目标**：发布第一个真正作品集项目。
**必须有**：README、架构图、Demo、测试、限制说明、部署说明、环境变量说明。
**验收**：别人能运行；你能在 10 分钟内讲清数据流和失败模式。
**求职**：把项目链接加入简历，继续投递。

## Day 22 — Tool Calling
**目标**：让 LLM 不只回答，还能调用程序。
**学习**：tool schema、arguments、tool result、validation；Hugging Face Agents Course https://huggingface.co/learn/agents-course/。
**实践**：做 calculator、search、local database 三个工具。
**产出**：`exercises/day22-tools/`。
**验收**：解释 function calling 和“模型自己执行代码”的区别。

## Day 23 — Agent loop
**目标**：理解 Agent 的最小原语。
**实践**：不用框架实现 `decide → tool → observe → decide` 循环；限制最大步数。
**产出**：`exercises/day23-agent-loop/`。
**验收**：能解释 Agent 与普通 chatbot 的核心差别。

## Day 24 — Tool reliability
**目标**：处理真实世界中的工具失败。
**实践**：模拟 timeout、invalid args、404、空结果；加入 retry、fallback、max steps。
**产出**：工具错误测试集。
**验收**：能解释为什么 agent 必须有 stop condition。

## Day 25 — Agent framework
**目标**：在理解 primitive 后再用框架。
**学习**：smolagents 或 LangGraph；https://huggingface.co/learn/agents-course/；https://langchain-ai.github.io/langgraph/。
**实践**：把 Day 23 agent 重写成框架版本。
**产出**：primitive vs framework 对比笔记。
**验收**：知道框架解决了什么、没有解决什么。

## Day 26 — Research Agent
**目标**：构建第二个作品集项目。
**流程**：用户问题 → 搜索 → 检索 → 提取 → 综合。
**实践**：Agent 能自己决定何时 search、何时使用私有 RAG。
**产出**：`projects/research-agent/` v0。
**验收**：20 个问题中能够完成规定工具动作。

## Day 27 — Web + RAG routing
**目标**：让 Agent 在多个知识来源之间选择。
**实践**：设计 router：current/web vs private/docs；记录每次路由。
**产出**：routing logic + test cases。
**验收**：能解释路由错误为什么会导致低质量答案。

## Day 28 — Agent state and memory
**目标**：理解 state。
**学习**：conversation state、task state、durable state。
**实践**：任务中断后恢复；保存用户研究主题和历史任务。
**产出**：persistent state implementation。
**验收**：能解释“聊天历史”和“任务状态”的区别。

## Day 29 — Agent evaluation
**目标**：评估 Agent 是否完成任务，而不仅是输出文本。
**实践**：20 个任务，定义 expected tools、expected outcome、max steps；统计成功率。
**产出**：`evaluation/agent_eval.md`。
**验收**：知道 tool-use accuracy、task success 和 final answer quality 不同。

## Day 30 — Research Agent v1.0
**目标**：第二个项目正式发布。
**必须有**：README、架构、Demo、evaluation、limitations。
**验收**：你能现场从空白解释一遍 Agent loop。
**求职**：继续投递，把 Research Agent 加入简历。

## Day 31 — Backend foundations
**目标**：从 notebook/script 进入服务端。
**学习**：REST、GET/POST、request validation、service boundaries；FastAPI https://fastapi.tiangolo.com/tutorial/。
**实践**：把 RAG 或 Agent pipeline 暴露成 FastAPI endpoint。
**产出**：API + OpenAPI 文档 + test。

## Day 32 — Database
**目标**：保存真实业务状态。
**学习**：SQL、table、primary key、index、CRUD。
**实践**：保存 users、conversations、messages；写查询。
**产出**：schema、migration、CRUD layer。
**验收**：能够画出数据表关系。

## Day 33 — Streaming
**目标**：理解 AI 产品为什么常用流式输出。
**实践**：后端逐 token/逐 chunk 向前端发送；处理断开与错误。
**产出**：streaming endpoint + UI。
**验收**：解释 streaming 如何降低用户感知延迟，但不能降低模型实际计算时间。

## Day 34 — Authentication and secrets
**目标**：最基本的生产安全。
**学习**：session/token 基础、env、secret handling。
**实践**：简单登录；API key 不进 Git；`.env` 加入 `.gitignore`。
**产出**：auth implementation + `.env.example`。
**验收**：在 GitHub history 中确认没有泄露 secret。

## Day 35 — XiaoYa 2 architecture
**目标**：重新设计你的心理学 AI 产品。
**架构**：UI / API / LLM / Retrieval / Memory / Persistence 分层。
**实践**：画系统图，明确每层输入输出。
**产出**：`projects/xiaoya-2/ARCHITECTURE.md`。
**验收**：你能解释为什么分层、每层如何独立替换。

## Day 36 — XiaoYa retrieval
**目标**：让产品拥有可靠的心理学知识库。
**实践**：导入高质量资料；加入 chunk metadata、citation、evaluation set。
**产出**：retrieval pipeline + 30-question eval。
**验收**：能识别 unsupported answer。

## Day 37 — XiaoYa tools
**目标**：给产品增加安全、有限的工具。
**实践**：加入时间/计算/笔记等低风险工具；设计 tool allowlist。
**产出**：tool registry + tests。
**验收**：用户文本不能任意触发系统级危险操作。

## Day 38 — XiaoYa memory
**目标**：让对话真正持续。
**实践**：保存 conversation history；加入用户偏好；区分会话记忆和长期资料。
**产出**：memory layer + tests。
**验收**：新会话与旧会话行为符合设计。

## Day 39 — UX and failure states
**目标**：学习“坏掉时产品是什么样”。
**实践**：empty state、no-source、timeout、rate limit、retry、tool failure、loading。
**产出**：`notes/failure-state-matrix.md` + UI。
**验收**：所有主要失败路径都有可理解的反馈。

## Day 40 — XiaoYa 2.0
**目标**：第三个项目发布。
**必须有**：线上 Demo、README、架构、evaluation、Demo 视频、限制说明。
**验收**：别人能独立体验；你能讲清产品价值和技术取舍。

## Day 41 — Docker
**目标**：理解容器，不追求 DevOps 专家水平。
**学习**：image、container、Dockerfile、compose；https://docs.docker.com/get-started/。
**实践**：把一个 FastAPI/LLM service 容器化。
**产出**：Dockerfile + compose + README。
**验收**：你能从 Dockerfile 解释镜像如何构建。

## Day 42 — FastAPI production basics
**目标**：让后端代码更像真实服务。
**学习**：settings、dependency injection、async、testing。
**实践**：分离 routers/services/models；加入 pytest。
**产出**：production-style API structure。
**验收**：测试可以一次运行；secret 来自环境变量。

## Day 43 — Redis/cache
**目标**：理解缓存和限流基础。
**学习**：cache、TTL、session、rate limiting concepts。
**实践**：缓存不会快速变化的 retrieval 结果；记录命中率。
**产出**：cache module + benchmark。
**验收**：知道缓存什么时候有害。

## Day 44 — Background jobs
**目标**：把耗时任务从请求线程中拿出去。
**学习**：queue、worker、background task。
**实践**：PDF ingestion 改成后台任务；前端查询状态。
**产出**：job state + worker implementation。
**验收**：用户不用一直等待 HTTP 请求结束。

## Day 45 — Logging and observability
**目标**：程序出问题时能回答“哪里坏了”。
**实践**：记录 request id、model、latency、token usage、retrieval count、tool errors。
**产出**：structured logging + `notes/observability.md`。
**验收**：模拟一次失败，根据日志定位问题。

## Day 46 — AI cost engineering
**目标**：理解一个 AI 产品为什么会贵。
**学习**：input/output token、model routing、context trimming、caching。
**实践**：估算 1k/10k/100k requests 成本；比较不同模型和 prompt。
**产出**：`notes/cost-model.md`。
**验收**：能说明降低成本的 5 种办法。

## Day 47 — AI security
**目标**：认识 LLM 特有攻击面。
**学习**：prompt injection、data leakage、secret exposure、input validation。
**实践**：攻击自己的 RAG/Agent；记录成功的攻击样例；加入防护。
**产出**：`security/adversarial-tests.md`。
**验收**：能解释为什么“system prompt 写禁止”本身不是完整安全方案。

## Day 48 — Evaluation harness
**目标**：把测试自动化。
**实践**：一条命令跑 retrieval、citation、agent tool-use、最终回答四类 regression tests。
**产出**：`evaluation/run_eval.py` + report。
**验收**：改 prompt 后能知道质量有没有退化。

## Day 49 — Portfolio cleanup
**目标**：把三个项目从“练习代码”变成“作品集”。
**实践**：删除死代码；加 type hints；统一 README；补 screenshots、architecture、setup、limitations。
**产出**：三个干净 repo/项目目录。
**验收**：陌生人能在 5 分钟理解项目价值和运行方式。

## Day 50 — Portfolio release
**目标**：正式建立求职作品集。
**实践**：固定 Demo URL；制作 2 分钟 Demo 视频；准备 GitHub profile。
**产出**：ResearchAI、Research Agent、XiaoYa 2.0 三项目最终版。
**求职**：继续大量投递。

## Day 51 — Transformer fundamentals
**目标**：达到 AI 工程岗位够用的原理水平。
**学习**：tokenization、embedding、attention、transformer blocks、training vs inference。
**实践**：不用资料画 Transformer 大致流程，并口头解释每一层。
**验收**：能回答“Attention 到底在计算什么”。

## Day 52 — RAG interview prep
**目标**：把实践转换成面试表达。
**准备**：top-k、chunking、reranking、hallucination、citation、evaluation、latency、cost。
**实践**：回答 20 道题并录音。
**产出**：`job-search/rag-interview.md`。

## Day 53 — Agent interview prep
**目标**：能从 primitive 层解释 Agent。
**准备**：tool calling、agent loop、state、memory、planning、failure handling。
**实践**：画 agent loop；解释为什么需要 max steps、retry 和 fallback。
**产出**：`job-search/agent-interview.md`。

## Day 54 — Python interview prep
**目标**：补足工程岗基础。
**准备**：list/dict/set/tuple、OOP、exceptions、iterators、generators、async、thread/process 基础。
**实践**：20 个 Python 题，至少 15 个不看答案完成。
**产出**：`job-search/python-20.md`。

## Day 55 — AI system design
**目标**：能设计一个真实 AI 服务。
**实践**：设计“AI 客服”和“AI Research Assistant”两个系统；考虑 ingestion、retrieval、cache、queue、DB、LLM、evaluation、security。
**产出**：两张 architecture diagrams + 设计说明。
**验收**：能解释瓶颈、成本、可扩展性。

## Day 56 — Project storytelling
**目标**：让面试官听得懂你的项目。
**实践**：每个项目准备 90 秒、5 分钟、15 分钟三个版本；结构固定为 problem → architecture → hard part → tradeoff → result → next step。
**产出**：`job-search/project-stories.md`。

## Day 57 — Resume + portfolio
**目标**：把“学习经历”变成“可雇佣证据”。
**实践**：用结果导向 bullet：built / deployed / evaluated / improved；加入 Demo 和 GitHub。
**产出**：resume v1 + portfolio page。
**求职**：每天 10–20 个针对性投递。

## Day 58 — Full mock interview
**目标**：验证是否真的能就业。
**实践**：60 分钟技术面 + 30 分钟项目 deep dive；全程录音；记录卡壳点。
**产出**：`job-search/mock-interview-58.md`。
**验收**：不能依靠稿子解释三个项目。

## Day 59 — Market feedback loop
**目标**：让市场决定最后补什么。
**实践**：整理过去所有面试问题、拒信、招聘 JD；统计最常出现的技能缺口；按岗位频率排序学习。
**产出**：`job-search/feedback-log.md`。
**原则**：不要因为“课程还没学完”停止投递。

## Day 60 — Employment readiness gate
**必须通过**：
- 3 个工作 AI 项目
- 至少 2 个部署 Demo
- clean public GitHub
- 能解释 LLM / RAG / Agent 核心原理
- 能独立 debug API / deployment / retrieval failures
- 能在 3–7 天内做一个新 AI MVP
- 有真实投递和面试反馈

**最终动作**：停止无期限准备，进入“边工作边学习”阶段。

---

# 每日固定工作流

## ① Learn — 1–2h
只学当天需要的知识。遇到陌生概念，追到能解释为止；不追求看完课程。

## ② Build — 2–3h
关掉教程，独立写。卡住时再查资料。优先官方文档。

## ③ Ship — 1–2h
把当天成果放到对应目录，写 README，保证能运行。

## ④ Commit — 5min
```bash
git status
git diff
git add .
git commit -m "Day XX: describe what changed"
git push
```

## ⑤ Reflect — 10min
记录三个东西：我今天学会了什么？哪里坏了？明天最重要的一件事是什么？

# 学习原则

1. 不以“看完课程”为完成标准，以“能独立做出来”为标准。
2. 每个概念都必须对应一个代码实验。
3. 每 7 天至少有一个可运行成果。
4. Day 15 开始边学边投，不等 60 天全部结束。
5. 面试暴露的知识缺口优先级高于课程目录。
6. 任何 API key、密码、token 都不能提交 Git。
