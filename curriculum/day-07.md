# Day 07 — Mini AI App

## 今天不再只练 API
把前 6 天的东西合成一个可以给别人使用的小产品：English Learning Assistant。

## 功能
用户输入单词，程序返回：词义、两个例句、中文记忆法、近义词、难度。结果至少有一个固定 JSON 结构。

## 实践步骤
1. 创建 `exercises/day07-mini-app/`。
2. 把 LLM 调用封装成函数。
3. 把 schema 与 prompt 分开。
4. 增加异常处理。
5. 做一个最简单的 CLI 或网页界面。
6. 写 README：安装、环境变量、运行命令、示例截图。

## 最重要的训练
不要复制教程结束。故意改需求，例如增加“只输出中文解释”和“难度必须是 1–5”。观察你是否可以自己修改程序。

## 验收
另一台电脑按照 README 可以运行；代码中没有 API key；遇到 API 错误不会直接崩掉。

## Git
今天至少做 2 个 commit：功能完成一次、README 完善一次。你开始学习“有意义的 commit”。

## 延伸材料
Python packaging: https://packaging.python.org/
