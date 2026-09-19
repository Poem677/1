# Git 学习笔记

记录 Git 学习过程中的常用命令和心得，持续更新。

## 一、Git 基础概念

- **工作区（Working Directory）**：本地写代码的目录。
- **暂存区（Staging Area / Index）**：`git add` 后文件进入的区域，表示准备提交。
- **版本库（Repository）**：`git commit` 后提交记录保存的地方，位于 `.git` 目录中。
- **远程仓库（Remote）**：托管在 GitHub 等平台上的仓库，用于多人协作和备份。

## 二、常用命令

### 1. 初始化仓库

```bash
git init
```

在项目目录中初始化一个空的 Git 仓库，生成 `.git` 目录。

### 2. 查看仓库状态

```bash
git status
```

查看当前工作区/暂存区的状态，能看出哪些文件被修改、哪些已暂存、哪些未跟踪。

### 3. 添加文件到暂存区

```bash
git add <文件名>      # 添加指定文件
git add .             # 添加当前目录所有变更
git add *.md          # 添加所有 md 文件
```

把工作区的改动放入暂存区，准备提交。

### 4. 提交修改

```bash
git commit -m "提交说明"
```

把暂存区的内容提交到版本库，`-m` 后面写清晰的提交信息。

### 5. 查看提交历史

```bash
git log               # 查看完整提交历史
git log --oneline     # 一行简洁显示提交历史
git log --stat        # 显示每次提交的文件变更统计
```

### 6. 分支操作

```bash
git branch              # 查看本地分支列表
git branch <分支名>     # 创建新分支
git checkout <分支名>   # 切换分支
git checkout -b <分支名> # 创建并切换分支
git merge <分支名>      # 合并分支
```

分支是 Git 的核心特性，可以在不影响主干的情况下并行开发。

### 7. 关联远程仓库

```bash
git remote add origin <仓库地址>   # 添加远程仓库，命名为 origin
git remote -v                     # 查看已关联的远程仓库
```

### 8. 推送与拉取

```bash
git push origin main       # 把本地 main 分支推送到远程
git push -u origin main    # 首次推送并建立跟踪关系
git pull origin main       # 拉取远程最新代码并合并
git clone <仓库地址>        # 克隆远程仓库到本地
```

### 9. 其他常用命令

```bash
git diff                 # 查看未暂存的改动内容
git diff --staged        # 查看已暂存的改动内容
git reset <文件名>        # 取消暂存
git rm <文件名>           # 删除文件
git config user.name "名字"    # 配置用户名（当前仓库）
git config user.email "邮箱"   # 配置邮箱（当前仓库）
```

## 三、典型工作流程

1. `git init` 初始化仓库
2. 创建/修改文件（README.md、源码等）
3. `git add .` 添加到暂存区
4. `git commit -m "说明"` 提交
5. `git remote add origin <仓库地址>` 关联远程
6. `git push -u origin main` 推送到 GitHub

## 四、踩坑记录与心得

- **提交信息要清晰**：用一句话说明本次改了什么，方便日后追溯。
- **先 status 再操作**：动手前先 `git status` 确认当前状态，避免误操作。
- **.gitignore 很重要**：临时文件、编译产物（如 .exe、.o）应加入 .gitignore，不要提交。
- **多提交、小提交**：把改动拆成多个有意义的提交，比一个大提交更好回滚和 review。
- **push 前先 pull**：协作时先 `git pull` 拉取最新代码，减少冲突。
