---
title: github之pull request的简单使用
date: 2018-04-26 19:12:43
tags:
---

## 第一步.在 github 上， 点击**Fork**来 fork 别人的代码

## 第二步.在本地，克隆你 fork 出来的代码

```bash
# clone代码
git clone git@github.com:<你的用户名>/<你fork的项目>.git

# 查看你连接的远端仓库
git remote -v
# git remote -v的显示结果
origin git@github.com:<你的用户名>/<你fork的项目>.git(fetch)
origin git@github.com:<你的用户名>/<你fork的项目>.git(push)
```

在你对项目做出一些修改后

```bash
# 提交到暂存区
git add .

# 创建并切换到add-file分支（分支名根据情况自己写）
git checkout -b add-file

# 提交到add-file分支
git commit -m '提交信息'

# 推送到到你的仓库add-file分支
git push origin add-file
```

## 第三步.在 github 上， 点击 **New pull request**（有时你可能需要点击 **compare across forks**）

选择 _base fork_（项目创始人的仓库）、_base_（项目创始人的仓库分支）、_head fork_（你的仓库）、_compare_（你的仓库分支，比如 add-file 分支，你往往只需要改动这里）。点击 **Create pull request**，填写 _title_（默认会将你的提交信息填入，可以手动修改）和 _comment_，点击 **Create pull request**。在项目创始人合并你的代码后（会有 email 通知），点击 **Delete branch** 删除分支

## 第四步.在本地，拉取项目创始人仓库最新的代码

```bash
# 添加项目创始人的仓库
git remote add upstream git@github.com:<项目创始人的用户名>/<你fork的项目>.git


# 查看你连接的远端仓库
git remote -v
# git remote -v的显示结果
origin git@github.com:<你的用户名>/<你fork的项目>.git(fetch)
origin git@github.com:<你的用户名>/<你fork的项目>.git(push)
upstream git@github.com:<项目创始人的用户名>/<你fork的项目>.git(fetch)
upstream git@github.com:<项目创始人的用户名>/<你fork的项目>.git(push)

# 切换到master分支
git checkout master

# 从项目创始人的仓库拉取代码到你的master分支
git pull upstream master

# 将最新的代码推送到自己的仓库的master分支
git push origin master
```
上面的例子演示了一个比较顺利的pull request，有时你的提交可能不符合规范，会被他人拒绝pull request，那么先从一个比较简单的项目着手，比如说[这里](https://github.com/mynane/PDF)。
