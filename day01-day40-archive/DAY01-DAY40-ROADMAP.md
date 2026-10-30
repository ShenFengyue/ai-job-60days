# Day 01–Day 40 路线索引

> 本文用于索引和归档，不替代原始每日课程手册。每一天更完整的学习目标、实践步骤、交付物和验收要求，请查看 [../curriculum/ALL-DAYS.md](../curriculum/ALL-DAYS.md)。

## 阶段一：Python、LLM API 与第一个应用（Day 01–07）

| Day | 主题 | 核心实践 / 产出 |
|---:|---|---|
| 01 | Python 基础与首次 AI 调用 | 可复用的 `call_llm()`、JSON 输出、项目环境 |
| 02 | HTTP 与 API | 带 timeout、异常处理和环境变量的 LLM API 调用 |
| 03 | Git / GitHub | 完成基础 Git 工作流和有意义的提交 |
| 04 | LLM 请求与响应 | CLI Chat，理解 messages、tokens、context |
| 05 | Prompt 设计 | 固定测试集比较多个 prompt |
| 06 | Structured Output | Pydantic / JSON 校验与错误处理 |
| 07 | English Learning Assistant | 完成一个可运行的最小 AI 应用 |

## 阶段二：Embedding、向量检索与 RAG（Day 08–21）

| Day | 主题 | 核心实践 / 产出 |
|---:|---|---|
| 08 | Embeddings | 句向量与相似度实验 |
| 09 | Vector Search | 本地向量检索、top-k |
| 10 | Document Ingestion | PDF 解析、清洗、元数据 |
| 11 | Chunking | 比较不同 chunk 策略 |
| 12 | Retrieval | 建立检索测试集 |
| 13 | First RAG | PDF 到检索增强问答的完整链路 |
| 14 | RAG Web App | 上传文档、问答、展示来源 |
| 15 | 开始求职 | 讲清 RAG 架构，开始针对性投递 |
| 16 | Retrieval Evaluation | golden set、precision、recall、recall@k |
| 17 | Metadata Filtering | 按文档、页码、日期、主题过滤 |
| 18 | Reranking | 对比向量初筛与重排序结果 |
| 19 | Citation Grounding | 答案引用来源，拒绝无依据结论 |
| 20 | Conversation Memory | 多轮对话指代与记忆层 |
| 21 | ResearchAI v1.0 | 发布第一个完整 RAG 作品集项目 |

## 阶段三：Tool Calling 与 Agent（Day 22–30）

| Day | 主题 | 核心实践 / 产出 |
|---:|---|---|
| 22 | Tool Calling | calculator、search、local database 工具 |
| 23 | Agent Loop | 原生 Python 实现 decide → tool → observe |
| 24 | Tool Reliability | timeout、invalid args、retry、fallback |
| 25 | Agent Framework | 用 smolagents 或 LangGraph 重构 Agent |
| 26 | Research Agent | 搜索、检索、提取、综合 |
| 27 | Web + RAG Routing | 在网络信息与私有文档间路由 |
| 28 | Agent State / Memory | 持久化任务状态与会话状态 |
| 29 | Agent Evaluation | 工具调用与任务成功率评估 |
| 30 | Research Agent v1.0 | 发布第二个作品集项目 |

## 阶段四：后端与 XiaoYa 产品化（Day 31–40）

| Day | 主题 | 核心实践 / 产出 |
|---:|---|---|
| 31 | Backend Foundations | 用 FastAPI 暴露 AI pipeline |
| 32 | Database | 用户、会话、消息的数据表与 CRUD |
| 33 | Streaming | 流式响应接口与前端 |
| 34 | Authentication / Secrets | 基础认证、环境变量和密钥管理 |
| 35 | XiaoYa 2 Architecture | UI、API、LLM、Retrieval、Memory、Persistence 分层 |
| 36 | XiaoYa Retrieval | 心理学知识库、引用检索与评估集 |
| 37 | XiaoYa Tools | 安全工具注册表与 allowlist |
| 38 | XiaoYa Memory | 对话历史、用户偏好与记忆层 |
| 39 | UX / Failure States | 空状态、无来源、超时、限流、重试等失败路径 |
| 40 | XiaoYa 2.0 Release | 发布产品、Demo、README、架构与评估报告 |

## 当前重置日期映射

根据用户 2026-10-05 的明确要求，当前执行进度使用以下映射，不再沿用仓库旧版日期表：

- Day 16 = 2026-10-05
- Day 17 = 2026-10-06
- Day 18 = 2026-10-07
- ...
- Day 40 = 2026-10-29

旧版课程文件的主题编号用于保留课程脉络；实际每日执行编号和日期以本映射及用户后续明确指令为准。
