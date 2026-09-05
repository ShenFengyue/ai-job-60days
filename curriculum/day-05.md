# Day 05 — Prompt Design

## 核心问题
Prompt 不是“会写漂亮话术”，而是把任务、上下文、约束和输出格式变成机器可执行的说明。

## 先学
理解四块：Instruction、Context、Examples、Output contract。观察同一个问题，在“自由回答”和“固定格式回答”下结果为什么不同。

## 实践
建立 `exercises/day05-prompts/`。
准备 10 个英语词汇测试题，分别写 3 个 Prompt：A 自由回答；B 明确步骤；C 明确 JSON 输出。每个 Prompt 跑同一套测试。

记录：正确性、完整性、格式稳定性、废话数量。不要凭感觉，做一个 Markdown 表格。

## 你必须理解
Prompt engineering 的关键不是越来越长，而是减少模型需要猜测的东西。任务边界越清晰，输出越容易评估。

## Git
`git status` → `git add .` → `git commit -m "Day 05: prompt evaluation"` → `git push`

## 验收
能够解释：为什么 few-shot 有效？什么时候应该拆任务？为什么输出格式本身也是接口？

## 材料
OpenAI prompting guidance: https://platform.openai.com/docs/guides/prompt-engineering
Git book: https://git-scm.com/book/en/v2
