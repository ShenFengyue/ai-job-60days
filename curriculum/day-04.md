# Day 04 — LLM 请求与响应

## 目标
理解一条 LLM 请求内部发生什么，并写一个最小 CLI Chat。

## 学习
模型不是“直接读你的话”，而是处理结构化消息。重点理解 `system`、`user`、`assistant`、token、context window、temperature、model。

## 材料
OpenAI API 文档：https://platform.openai.com/docs/ ；Hugging Face LLM Course：https://huggingface.co/learn/llm-course/chapter1/1

## 实践
建立 `exercises/day04-llm-cli/main.py`：
- 从命令行读取用户输入
- 使用固定 system prompt
- 调用模型
- 连续对话 5 轮
- 支持从环境变量切换模型
- 错误时给出清晰提示

## 思考
为什么聊天记录越长越贵？system prompt 和 user prompt 为什么要分开？temperature 改变的是知识还是采样行为？

## 验收
不用看资料，画出：user → API → model → response；解释 context window 和 token 的关系。

## Git
提交：`git add . && git commit -m "Day 04: build LLM CLI" && git push`。