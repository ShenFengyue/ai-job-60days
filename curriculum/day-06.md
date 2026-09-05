# Day 06 — Structured Output

## 今天的核心
真实 AI 应用不能只接收一段自然语言；程序需要可靠的数据结构。今天学习 JSON、schema、Pydantic 和失败重试。

## 学习
理解：LLM 输出文本 → parser → validation → typed object。阅读 Pydantic Models 文档，并观察字段类型、必填字段、默认值和校验。

## 实践
做 `exercises/day06-structured-output/`：输入一个英文单词，让模型返回 `word / definition / examples / mnemonic / difficulty`。故意让模型输出错误 JSON，验证程序能检测并给出明确错误。

再加入一次 retry：第一次解析失败，第二次要求模型严格修复格式。

## 验收
你能解释“模型会说话”和“模型给程序返回可靠数据”的区别；能指出为什么 JSON.parse 成功并不代表数据正确。

## Git
完成后 `git add . && git commit -m "Day 06: structured output" && git push`。

## 材料
Pydantic: https://docs.pydantic.dev/latest/concepts/models/
