# Day 02 — HTTP + APIs

## 今天的目标
今天不是“看懂 API”，而是让你能自己写一个稳定的 Python → LLM API 程序。

## 先理解 4 个东西
- HTTP：程序之间传消息的规则。
- URL：你要访问的地址。
- Headers：附加信息，例如认证。
- JSON：最常见的数据格式。

一次 AI 请求可以理解成：
`Python → HTTPS → API Server → Model → JSON Response → Python`

## 学习材料
1. Python `requests` Quickstart：https://requests.readthedocs.io/en/latest/user/quickstart/
2. HTTP overview：https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview
3. 你所使用模型供应商的最新 API 文档。

## 实践
创建 `exercises/day02-api/main.py`。
实现：
1. 从环境变量读取 API Key。
2. 向模型发送一条消息。
3. 设置 timeout。
4. 处理网络异常和 HTTP 错误。
5. 打印模型回复。

不要把 API Key 写进代码。

## 代码骨架
```python
import os
import requests

API_KEY = os.environ["API_KEY"]
# TODO: build request
```

## Git
第一次练习：修改文件后运行：
```bash
git status
git add .
git commit -m "Day 02: call LLM API"
git push
```

## 验收
你能回答：什么是 HTTP？API Key 为什么不能上传 GitHub？timeout 为什么重要？

## 今日成果
`exercises/day02-api/` 能在另一台电脑按 README 配置环境后运行。