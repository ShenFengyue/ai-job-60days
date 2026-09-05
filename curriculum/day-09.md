# Day 09 — Vector Search

## 学什么
Embedding 只是把文本变成向量；今天学习如何保存向量并做 top-k 检索。理解 index、query、similarity、metadata。

## 动手
用 FAISS 或 Chroma 任选一个。准备 50 条自己的学习笔记，每条带 `source` 和 `topic`。建立索引，输入 10 个问题，返回最相似的 5 条，并显示分数与来源。

## 思考
比较关键词搜索和语义搜索：找不到同义词时谁更好？加入一个完全无关的文本，看 top-k 是否会被污染。

## 产出
`exercises/day09-vector-search/`：`main.py`、`data.json`、`README.md`、结果截图。

## 验收
能解释“向量库解决的不是生成，而是检索”；能说明为什么 top-k 过大可能把噪声送进上下文。

## 材料
Sentence Transformers semantic search: https://www.sbert.net/examples/sentence_transformer/applications/semantic-search/README.html
Chroma docs: https://docs.trychroma.com/
