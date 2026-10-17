# Day 03 — Git and GitHub from zero

## 今天的目标
今天把 Git 从“看起来很吓人”变成 5 个命令：`status / add / commit / log / push`。

## 核心模型
你的电脑 = working tree；Git = 本地版本记录；GitHub = 远程仓库。
流程：改文件 → `git status` → `git add` → `git commit` → `git push`。

## 学习材料
Git Book：https://git-scm.com/book/en/v2
GitHub Git basics：https://docs.github.com/en/get-started/learning-to-code/getting-started-with-git

## 实践
1. 在电脑安装 Git。
2. `git clone https://github.com/ShenFengyue/ai-job-60days.git`
3. 新建 `exercises/day03-git/README.md`。
4. 写下今天学到的 5 个命令。
5. `git status` 查看变化。
6. `git add .` 暂存。
7. `git commit -m "Day 03: learn Git basics"` 保存。
8. `git push` 上传。
9. 打开 GitHub 验证文件出现。

## 认识另外 3 个命令
`git diff` 看修改；`git log --oneline` 看历史；`git pull` 拉回远程更新。

## 不要急着学
branch、merge、rebase 今天只知道名字即可。

## 验收
你能解释：commit 和 push 的区别；GitHub 删除文件后本地为什么不会自动删除；为什么 `.env` 不应该提交。

## 今日成果
完成一次真实的 clone → edit → add → commit → push 全流程。