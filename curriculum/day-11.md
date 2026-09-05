# Day 11 — Chunking

## 核心
Chunk 是 RAG 的基本检索单位。太大，搜索不精确；太小，语义不完整。

## 实践
对同一篇论文测试 300/500/1000 token，overlap 0%/15%。建立 15 个问题，比较 top-5 是否包含支持答案的 chunk。

## 学习
chunk size、overlap、semantic boundary、标题层级。不要寻找“永远最佳”的 chunk size，而是用自己的测试集做选择。

## 产出
`notes/chunking-experiment.md` + 结果表 + 5 个失败案例。

## 验收
能解释三种参数如何改变 retrieval 质量。