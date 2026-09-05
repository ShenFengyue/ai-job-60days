# Day 10 — Document Ingestion

**目标**：把 PDF、TXT 等真实资料变成干净且可追踪的数据。

**学习**：理解 parsing、cleaning、metadata；每条记录至少包含 `text/source/page/title`。

**实践**：准备 3 篇心理学论文，解析后输出 JSONL。处理空页、乱码、页眉页脚。写 `load_pdf()` 与 `save_jsonl()`。

**检查**：打印 3 个最短和最长 chunk，确认页码没有丢失。

**产出**：`exercises/day10-ingestion/` + README + sample.jsonl。

**验收**：能解释为什么原始 PDF 不能直接进入向量库，以及为什么 page metadata 对 citation 很重要。