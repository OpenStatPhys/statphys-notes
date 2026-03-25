# Git/GitHub基础

## Git / GitHub 基本操作说明手册

本手册说明Git/GitHub的基本工作流程，适用于个人开发和团队协作。

---

### 1. 基本概念

Git 工作通常涉及三个层次：

| 层次                | 含义   |
| ----------------- | ---- |
| Remote (GitHub)   | 远程仓库 |
| Local repository  | 本地仓库 |
| Working directory | 工作目录 |

常见分支：

* `main`：主分支
* `my-feature`：功能分支

基本原则：

* 不要直接在 `main` 上开发
* 每个功能使用独立分支
* 经常提交
* 经常同步

---

### 2. 克隆仓库

开始工作时，从远程仓库克隆：

```bash
git clone <repo-url>
cd repo
```

---

### 3. 创建功能分支

开始开发新功能：

```bash
git checkout -b my-feature
```

含义：

* 创建新分支
* 切换到该分支

原则：

* 每个功能一个分支
* 不在 `main` 上开发 （重要）

---

### 4. 修改代码并提交

修改代码后：

```bash
git diff
git add <files>
git commit -m "message"
```

建议：

* 每做一次有意义的修改就提交一次
* commit 可以很小，但要清楚

示例：

```bash
git add .
git commit -m "Add new function"
```

---

### 5. 推送到 GitHub

把本地分支推送到远程：

```bash
git push origin my-feature
```

推送后，远程仓库中会出现新的分支 `my-feature`，然后可以创建 Pull Request。

---

### 6. main 更新后的同步流程

有时远程 `main` 更新了，需要把最新内容同步到自己的功能分支。

#### Step 1：切换到 main

```bash
git checkout main
```

#### Step 2：拉取最新 main

这一步关键。
```bash
git pull origin main
```

#### Step 3：切回功能分支

```bash
git checkout my-feature
```

#### Step 4：基于最新 main 进行 rebase
(有冲突才会用到)
```bash
git rebase main
```

如果出现冲突：

1. 手动修改冲突文件
2. 标记为已解决
3. 继续 rebase

```bash
git add .
git rebase --continue
```

#### Step 5：推送更新后的分支
（常用）
```bash
git push origin my-feature
```

如果远程已有旧历史，rebase 后通常需要：

```bash
git push --force-with-lease origin my-feature
```

---

### 7. Pull Request 与合并

在 GitHub 上通常流程如下：

1. 创建 Pull Request
2. 进行 Review
3. 合并到 `main`

推荐使用：

* **Squash and merge**

优点：

* `main` 历史更干净
* 更便于管理和回顾

---

### 8. 合并完成后的清理

#### 删除远程分支

在 GitHub 页面点击：

* `Delete branch`

#### 删除本地分支

```bash
git checkout main
git branch -d my-feature
```

---

### 9. 更新本地主分支

合并后，把本地 `main` 更新到最新状态：

```bash
git pull origin main
```

---

### 10. 推荐完整流程

```text
clone
↓
checkout -b feature
↓
edit
↓
commit
↓
push
↓
open pull request
↓
main changed? → pull main + rebase
↓
push updated branch
↓
merge
↓
delete branch
↓
pull main
```

---

### 11. 最佳实践

* 不直接修改 `main`
* 每个功能一个分支
* 小步提交
* 经常同步远程更新
* 合并前先同步 `main`
* 合并后删除无用分支
* commit message 要简洁明确

---

### 12. 常用命令速查

```bash
git clone <url>

git checkout -b my-feature

git add .
git commit -m "message"

git push origin my-feature

git checkout main
git pull origin main

git checkout my-feature
git rebase main
git push --force-with-lease origin my-feature

git checkout main
git branch -d my-feature
```

### 13. 简要说明

一个典型开发周期如下：

1. 从远程仓库克隆代码
2. 创建功能分支
3. 修改代码并提交
4. 推送到 GitHub
5. 创建 Pull Request
6. 如果主分支有更新，先同步再 rebase
7. 合并到主分支
8. 删除功能分支并更新本地 `main`

这样可以保证：

* 主分支稳定
* 开发过程清晰
* 团队协作更顺畅

