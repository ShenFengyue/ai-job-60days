# Day 08 — Embeddings

## 核心
Embedding 把文本映射成向量，用于“按意义搜索”而非只按关键词匹配。你今天不学线性代数推导，先把数据流跑通。

## 学习
阅读 Sentence Transformers quickstart 和 semantic search。理解 corpus、query、vector、similarity、top-k。

## 实践
准备 30 条心理学/AI 句子。用 `sentence-transformers` 编码；输入 10 个查询；返回最相似的 5 条，并打印相似度。把结果保存成 JSON。

## 实验
故意加入关键词完全不同但意思相近的句子，观察语义搜索为什么可能找到它。

## 验收
你能画出 `text → embedding → similarity → top-k`；能解释 embedding 和普通字符串搜索的差别。

## 材料
https://www.sbert.net/docs/quickstart.html
https://www.sbert.net/examples/sentence_transformer/applications/semantic-search/README.html
