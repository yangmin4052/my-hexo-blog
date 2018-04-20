---
title: 如何搭建自己的hexo博客（上）
date: 2018-04-20 13:57:37
tags:
---
本篇讲解如何在github主页创建你的hexo博客，
下篇讲解如何通过gh-pages创建你的hexo博客，见[如何搭建自己的hexo博客（下）](https://yangmin4052.github.io/2018/04/20/如何搭建自己的hexo博客（下）/)

## 第一步 安装hexo的命令行工具
```
$ npm install -g hexo-cli
$ npm install -g hexo-cli@1.0.4 // 如果你想安装指定的版本

```
## 第二步 hexo初始化

```
$ hexo init <folder>
$ cd <folder>
$ npm install
```
## 第三步 配置_config.yml
```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 我的Hexo博客
subtitle:
description:
author: 杨敏
language:
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://yangmin4052.github.io
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:yangmin4052/yangmin4052.github.io.git
  user: yangmin4052
```

## 第四步 在github新建一个仓库
你的仓库名有严格的限制<你的用户名>.github.io，比如我的账户为yangmin4052，所以我的仓库必须是yangmin4052.github.io
## 第五步 写博客，发表博客
```
// 在你的<folder>中执行一下命令
// 创建markdown文档
$ hexo new "新的博客名称"

// 启用hexo本地服务器，查看项目本地状态
$ hexo server
$ hexo s // 简写

// 生成html静态文件
$ hexo generate
$ hexo g // 简写

// 将html静态文件上传到你的github对应的仓库分支上，但现在你的源代码现在并没有上传
$ hexo deploy
$ hexo d // 简写

```
## 第六步 保存源代码
博客的html静态文件默认使用了<你的用户名>.github.io仓库的master分支，如果你需要将你的源代码也放置到该仓库，你需要新建一个分支，比如我创建的分支名叫hexo，(当然，如果你想把你的源代码放到别的地方，比如gitlab，也完全没有问题)，命令如下：
```
// 初始化本地仓库
$ git init

// 创建分支hexo并切换到分支hexo
$ git checkout -b hexo

// 暂存文件
$ git add .

// 提交文件
$ git commit -m '你的提交信息'

// 为本地仓库添加远程仓库连接
$ git remote add origin git@github.com:<你的用户名>/<你的用户名>.github.io.git
// 比如，我的仓库对应的命令是：
$ git remote add origin git@github.com:yangmin4052/yangmin4052.github.io.git

// 推送文件
git push -u origin hexo

```
## 第七步 如果你换了台电脑，clone你的代码

```
// clone你的代码
// 如果你对你的文件夹叫<你的用户名>.github.io没有意见，可以执行以下命令：
$ git clone git@github.com:<你的用户名>/<你的用户名>.github.io.git

// 如果你想在clone你的代码的时候将代码放到指定的文件夹，比如my-blog文件夹，可以执行以下命令：
$ git clone git@github.com:<你的用户名>/<你的用户名>.github.io.git my-blog

// 打开项目文件夹，与上面两条命令一一对应
$ cd <你的用户名>.github.io.git
或
$ cd my-blog

// 切换到hexo分支
$ git checkout hexo

// 在新电脑上安装依赖
$ npm install

```
## 第八步 重复第五步
## 第九步 参见第六步
```
// 暂存文件
$ git add .

// 提交文件
$ git commit -m '你的提交信息'

// 推送文件
$ git push
```
有的小伙伴可能不想在主页写博客，说的就是我自己，所以我准备了[如何搭建自己的hexo博客（下）](https://yangmin4052.github.io/2018/04/20/如何搭建自己的hexo博客（下）/)。