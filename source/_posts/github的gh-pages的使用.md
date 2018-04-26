---
title: github的gh-pages的使用
date: 2018-04-26 18:34:31
tags:
---

* 如果你在 github 开启了一个前端开源项目，你想其他人即使不拉取你的代码的情况下也可以查看页面效果，你需要使用 github 提供的 gh-pages 分支，下面教你如何使用首先在 github 官网创建你的仓库，假设你创建的是 gh-pages-test

在你的本地

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<你的用户名>/gh-pages-test.git
git push -u origin master
```

此时你的源代码已经上传至 github

假设你使用的是 vue-cli 生成的项目，当你执行

```bash
npm run build
```

之后，会生成一个 dist 文件夹，你可以进行以下操作

```bash
# 打开dist文件夹
cd ./dist/

# git初始化
git init

# 创建并切换到分支gh-pages
git checkout -b gh-pages

追踪代码
# git add .

# 提交代码
git commit -m "first commit"

# 关联远程仓库
git remote add origin git@github.com:<你的用户名>/gh-pages-test.git

# push代码到gh-pages分支
git push -u origin gh-pages

# 回到项目目录
cd ..
```

当然，你也可以使用其他方式，比如这篇[如何用 Github 的 gh-pages 分支展示自己的项目](https://www.cnblogs.com/MuYunyun/p/6082359.html)，如果不懂 subtree 你可以看看[用 Git Subtree 在多个 Git 项目间双向同步子项目，附简明使用手册](https://segmentfault.com/a/1190000003969060)
