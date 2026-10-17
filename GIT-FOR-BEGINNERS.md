# Git for Absolute Beginners

你不需要先“学会 Git”才能开始这个 60 天计划。

本文件只教你完成一件事：

```text
电脑上的代码
   ↓
Git 记录版本
   ↓
GitHub 保存远程副本
```

## 1. Git 和 GitHub

**Git**：安装在你电脑上的版本控制工具，负责记录项目变化。

**GitHub**：网上的代码托管平台，负责保存你的远程 repository。

所以：

```text
你电脑
ai-job-60days/
      ↓
     Git
      ↓ push
GitHub
ShenFengyue/ai-job-60days
```

## 2. 第一次使用：先 Clone

不要在电脑上随便新建一个同名文件夹。

用 GitHub Desktop：

1. 登录 GitHub。
2. `File → Clone repository`。
3. 选择 `ShenFengyue/ai-job-60days`。
4. 选择电脑上的保存位置。
5. 点击 `Clone`。

完成后，你拥有一个**本地仓库**。

例如：

```text
D:\AI\ai-job-60days
```

以后主要在这个文件夹里写代码。

## 3. 最重要的概念

把 Git 想成一个游戏存档系统。

```text
工作区
  ↓
修改文件
  ↓
add = 选择要存档的东西
  ↓
commit = 创建存档
  ↓
push = 上传云端
```

### Working tree

你当前正在修改的文件。

### Staging area

通过 `git add` 选中、准备进入下一次 commit 的修改。

### Commit

一个具体的历史快照。

### Remote

GitHub 上的远程 repository。

## 4. 你每天只需要这几个命令

先进入仓库目录：

```powershell
cd D:\AI\ai-job-60days
```

查看状态：

```powershell
git status
```

看看修改：

```powershell
git diff
```

把修改加入下一次 commit：

```powershell
git add .
```

创建 commit：

```powershell
git commit -m "Day 01: first AI API app"
```

上传 GitHub：

```powershell
git push
```

查看历史：

```powershell
git log --oneline
```

## 5. 第一个完整例子

你修改：

```text
exercises/day01-python/main.py
```

然后：

```powershell
git status
```

你会看到 `main.py` 被修改。

再：

```powershell
git diff
```

确认你到底改了什么。

然后：

```powershell
git add .
git commit -m "Day 01: add first Python exercise"
git push
```

刷新 GitHub。

你就会看到新版本。

## 6. 为什么 commit 要写清楚？

因为未来你会看到：

```text
9b12a3f Day 01: add first Python exercise
2a81c1e Day 01: add LLM API call
71f2d90 Day 02: add API error handling
```

这就是你的开发历史。

不要写：

```text
update
fix
test
asdf
```

推荐：

```text
Day 01: add Python input example
Day 01: call LLM API
Day 02: handle API timeout
Day 08: add embedding search
```

## 7. GitHub Desktop 怎么做？

如果你完全不想敲命令，可以先用 GitHub Desktop。

修改文件以后，它会列出 changed files。

你依次做：

```text
确认修改
↓
填写 Summary
↓
Commit to main
↓
Push origin
```

命令行版本只是：

```text
git status
→ 看变化

git add .
→ 选择变化

git commit -m "..."
→ 存档

git push
→ 上传
```

两者做的是同一套核心事情。

## 8. 今天不要学这些

暂时不要碰：

```text
git rebase
git reset --hard
git cherry-pick
git reflog
git submodule
复杂 branch workflow
复杂 pull request workflow
```

这些不是 Day 1 的瓶颈。

## 9. 如果 push 报错

**不要连续乱试命令。**

把完整报错复制给 ChatGPT。

尤其不要在没理解的情况下使用：

```powershell
git push --force
```

## 10. 你最终只需要形成肌肉记忆

每天完成代码后：

```powershell
git status
git diff
git add .
git commit -m "描述今天完成的事情"
git push
```

以后你每天都重复这五步。

Git 官方和 GitHub 官方都把 commit 视为保存项目变化历史的核心工作流；GitHub Desktop 则提供了可视化方式来完成相同的基本操作。
