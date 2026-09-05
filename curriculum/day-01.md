# Day 01 — Python + API：写出第一个 AI 程序

日期：**2026-09-05**

今天不是“看完 Python 教程”。今天的唯一目标是：**你能在自己的电脑上创建一个 Python 项目，运行一个脚本，并理解它是怎么调用 AI API 的。**

## 今天的最终成果

完成后，你的本地目录应当类似：

```text
ai-job-60days/
└── exercises/
    └── day01-python/
        ├── main.py
        ├── README.md
        ├── requirements.txt
        └── .env.example
```

`main.py` 至少实现：

```text
用户输入问题
    ↓
Python 程序
    ↓
调用 LLM API
    ↓
打印回答
```

---

## 0. 今天你要先学会一个东西：Git 是什么？

先别害怕 Git。

你可以先把它理解成：**给代码做“存档”的工具。**

GitHub 是网上保存这些代码和存档的地方。Git 本身负责记录你电脑上的代码变化；GitHub 则托管远程仓库。citehttps://docs.github.com/en/get-started/using-github/what-is-github

最基本的循环只有 4 个动作：

```text
写代码
 ↓
git add
 ↓
git commit
 ↓
git push
 ↓
GitHub 上出现你的最新代码
```

### 四个词

**repository / repo**：项目文件夹 + Git 的历史记录。

**add**：告诉 Git，“我准备把这些修改放进下一次存档”。

**commit**：创建一个版本快照。

**push**：把本地的 commit 上传到 GitHub。

GitHub 官方文档也把 Git 描述为用于追踪文件变化的版本控制系统，并把 GitHub 作为远程托管和协作平台。citehttps://docs.github.com/en/get-started/learning-to-code/getting-started-with-git

---

# 1. 安装/检查工具

你需要：

- Python
- VS Code
- Git
- GitHub Desktop（今天推荐用它学 Git，先不要被命令行吓到）

GitHub 官方入门文档明确提供 GitHub Desktop 作为不熟悉命令行时的可视化 Git 工作方式。citehttps://docs.github.com/en/get-started/learning-to-code/getting-started-with-git

在 PowerShell / CMD 中分别执行：

```powershell
python --version
git --version
```

看到版本号即可。

---

# 2. 把这个 GitHub 仓库下载到电脑

打开 GitHub Desktop：

1. 登录你的 GitHub 账号。
2. 选择 **Clone a repository**。
3. 选择 `ShenFengyue/ai-job-60days`。
4. 选择一个你容易找到的位置，例如：

```text
D:\AI\ai-job-60days
```

5. 点击 Clone。

这一步完成后，你电脑上就有一个真正的项目文件夹了。

你以后写代码，**主要在电脑这个文件夹里写**，不是直接在 GitHub 网页里写。

GitHub 官方也把这一模式描述为：本地 repository 保存工作，remote repository 托管在 GitHub；通过 push 把 commits 发布到远程仓库。citehttps://docs.github.com/en/get-started/git-basics/about-remote-repositories

---

# 3. 第一个 Python 环境

在 VS Code 打开这个仓库。

打开终端：

```powershell
cd D:\AI\ai-job-60days
python -m venv .venv
```

Windows PowerShell 激活：

```powershell
.\.venv\Scripts\Activate.ps1
```

如果 PowerShell 因执行策略拒绝激活，可以先跳过激活，或者改用 VS Code 的 Command Prompt 终端。今天重点是学 Python 和 Git，不要卡死在环境配置上。

然后创建：

```text
exercises/day01-python/
```

---

# 4. 今天真正要学的 Python

只学够今天项目使用的部分：

### 函数

```python
def greet(name):
    return f"Hello, {name}!"
```

你必须明白：

```text
输入 → 函数 → 输出
```

### 字典

```python
user = {
    "name": "Grayson",
    "age": 23,
}
```

理解：key → value。

### List

```python
questions = [
    "什么是人工智能？",
    "什么是 RAG？",
]
```

### JSON

理解 Python 字典和 JSON 数据之间的关系。

### 异常

```python
try:
    ...
except Exception as e:
    print(e)
```

### import

理解：把另一个模块里的代码拿进来使用。

### pip

知道它是 Python 包管理工具，今天只需要会：

```powershell
pip install package-name
```

Python 官方教程可以用来查语法和基础概念；不要试图一天从头读完。citehttps://docs.python.org/3/tutorial/

---

# 5. 第一个 AI 程序

创建：

```text
exercises/day01-python/main.py
```

第一版甚至可以先不接 API，先完成：

```python
question = input("Ask AI: ")
print("你的问题是：", question)
```

运行：

```powershell
python exercises/day01-python/main.py
```

确认你理解了：

```text
input()
↓
变量
↓
print()
```

然后再升级成 API 调用。

---

# 6. API 你到底在学什么？

先记住一句话：

> **API 就是你的程序和另一个程序说话的接口。**

你的程序：

```text
“请帮我回答这个问题。”
```

AI 服务：

```text
“好的，这是回答。”
```

真正做 AI 应用时，你不是天天手工打开网页问 ChatGPT，而是让 Python 程序代表用户向模型发送请求，然后继续处理返回结果。

今天可以选你已有的 DeepSeek API，也可以使用其他兼容 OpenAI 风格 API 的服务。

**绝对不要把 API Key 写进 `main.py` 并上传 GitHub。**

使用环境变量，例如：

```text
.env
```

并把 `.env` 放进 `.gitignore`。

---

# 7. 今天的练习顺序

不要跳。

### Exercise 1

写一个 Python 程序：

```text
输入姓名
输入年龄
输出一句完整介绍
```

### Exercise 2

写一个函数：

```python
def summarize(text):
    ...
```

先不用 AI，返回字符串即可。

### Exercise 3

加入 LLM API。

实现：

```text
用户输入一句问题
↓
Python
↓
LLM API
↓
打印回答
```

### Exercise 4

让程序连续问 3 次问题，并把结果保存为 JSON：

```json
[
  {
    "question": "...",
    "answer": "..."
  }
]
```

---

# 8. Git：你今天只学 5 个命令

如果你愿意用命令行，这是今天最重要的五个：

```powershell
git status
git add .
git commit -m "Day 01: first AI API app"
git push
git log --oneline
```

含义：

```text
git status
= 看现在发生了什么变化

 git add .
= 把修改加入下一次存档候选

 git commit -m "..."
= 创建一个版本快照

 git push
= 上传到 GitHub

 git log --oneline
= 查看历史存档
```

GitHub 官方入门流程也是围绕修改、commit、再把 commit 推到远程仓库展开的。citehttps://docs.github.com/en/get-started/learning-to-code/getting-started-with-git

**今天不用学 branch、merge、rebase、PR。**

那些以后再学。

---

# 9. 第一次 Commit

完成 `main.py` 后：

```powershell
git status
git add .
git commit -m "Day 01: Python and first AI app"
git push
```

然后刷新：

```text
https://github.com/ShenFengyue/ai-job-60days
```

你应该能看到自己的文件已经出现在 GitHub。

这就是你第一次真正使用 Git。

---

# 10. 今天的 Git 实验

故意修改 `main.py` 一行。

然后运行：

```powershell
git status
```

你会看到 Git 告诉你：文件发生了变化。

再运行：

```powershell
git diff
```

你会看到**到底改了什么**。

然后：

```powershell
git add .
git commit -m "Day 01: update program"
git push
```

现在你已经亲自完成：

```text
修改
↓
diff
↓
add
↓
commit
↓
push
↓
GitHub
```

这就是 Git 最核心的工作流。

---

# 11. 今日学习材料

### 必看 1：Python 官方 Tutorial

https://docs.python.org/3/tutorial/

今天重点看：

- 3. An Informal Introduction to Python
- 4. More Control Flow Tools
- 5. Data Structures
- 6. Modules

**不用通读。只查你今天遇到的语法。**

Python 官方文档当前版本为 3.14.7，教程和语言参考都在官方文档中维护。citehttps://docs.python.org/3/

### 必看 2：GitHub — Getting started with Git

https://docs.github.com/en/get-started/learning-to-code/getting-started-with-git

重点理解：repository / commit / branch / remote。

### 必看 3：GitHub Skills — Introduction to GitHub

https://skills.github.com/

这是互动式学习，不要只看。

### 查阅：Git 官方书籍

https://git-scm.com/book/en/v2

今天不用啃。

---

# 12. 今日时间安排

推荐 6–8 小时：

```text
Python 基础              1.5 h
Git/GitHub                1.0 h
API 原理                  0.5 h
编码                      3.0 h
Git 提交实验              1.0 h
复盘                      0.5 h
```

如果环境配置卡住，不要把 3 小时浪费在配置上。把问题贴给 ChatGPT，让它带你排错。

---

# 13. Day 1 验收标准

完成下面全部内容才算 Day 1：

- [ ] 能解释 Python 函数、List、Dict、JSON
- [ ] 能自己创建并运行 `.py` 文件
- [ ] 能创建 Python 虚拟环境
- [ ] 理解 API 是什么
- [ ] 能让 Python 调用一次 LLM API
- [ ] API Key 不出现在公开 GitHub 文件里
- [ ] 会 `git status`
- [ ] 会 `git add .`
- [ ] 会 `git commit`
- [ ] 会 `git push`
- [ ] 能在 GitHub 上看到自己的 commit
- [ ] 能用 `git diff` 看出自己改了什么

## 最终验收题

不用查资料，回答下面 5 个问题：

1. Git 和 GitHub 到底是什么关系？
2. `git add` 和 `git commit` 的区别是什么？
3. 为什么 API Key 不能直接写进 GitHub？
4. Python 程序调用 LLM API 时，中间发生了什么？
5. 如果你明天继续改 `main.py`，怎样把新版本同步到 GitHub？

如果这 5 个问题你能讲清楚，**Day 1 通过。**

---

# 14. 今天最后做一件事

在 `exercises/day01-python/README.md` 写下：

```markdown
# Day 01

## I learned

## What I built

## What broke

## What I still don't understand

## Git commit

## Screenshot
```

这不是形式主义。

60 天之后，这些文件会变成你的学习轨迹、项目证据和面试素材。
