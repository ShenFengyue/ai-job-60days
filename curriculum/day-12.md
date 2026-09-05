# Day 12 — Retrieval

## 目标
从“找到相关文字”变成“找到能支持答案的证据”。

## 实践
制作 20 个黄金问题，为每题标出正确 supporting chunk。输出 top-1/3/5，记录是否命中。

专门测试同义词、模糊问题、跨章节问题、数字问题和信息不足问题。

## 调试顺序
query → embedding → index → metadata → top-k。不要一失败就换模型。

## 产出
`evaluation/retrieval-test-set.json` + `notes/retrieval-failures.md`。

## 验收
能区分 retrieval failure 与 generation failure。