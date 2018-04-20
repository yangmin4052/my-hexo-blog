---
title: 如何搭建自己的hexo博客（下）
date: 2018-04-20 13:57:53
tags:
---
上篇讲解如何在github主页创建你的hexo博客，见[如何搭建自己的hexo博客（上）](https://yangmin4052.github.io/my-hexo-blog/2018/04/20/%E5%A6%82%E4%BD%95%E6%90%AD%E5%BB%BA%E8%87%AA%E5%B7%B1%E7%9A%84hexo%E5%8D%9A%E5%AE%A2%EF%BC%88%E4%B8%8A%EF%BC%89/)，
本篇讲解如何通过gh-pages创建你的hexo博客
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
keywords:
author: 杨敏
language:
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://yangmin4052.github.io/my-hexo-blog
root: /my-hexo-blog/
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
  repo: git@github.com:yangmin4052/my-hexo-blog.git
  branch: gh-pages
  user: yangmin4052
```

## 第四步 在github新建一个仓库
注意和你的_config.yml文件中的配置相对应，比如我的仓库叫my-hexo-blog
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
博客的html静态文件使用了my-hexo-blog仓库的gh-pages分支（注意这里的分支名必须是gh-pages），如果你需要将你的源代码也放置到该仓库，你可以把你的源代码放置到master分支上，命令如下：
```
// 初始化本地仓库
$ git init

// 暂存文件
$ git add .

// 提交文件
$ git commit -m '你的提交信息'

// 为本地仓库添加远程仓库连接
$ git remote add origin git@github.com:<你的用户名>/<你的用户名>.github.io.git
// 比如，我的仓库对应的命令是：
$ git remote add origin git@github.com:yangmin4052/yangmin4052.github.io.git

// 推送文件
git push -u origin master

```
## 第七步 如果你换了台电脑，clone你的代码

```
// clone你的代码
// 如果你对你的文件夹叫<你的用户名>.github.io没有意见，可以执行以下命令：
$ git clone git@github.com:<你的用户名>/<你的用户名>.github.io.git

// 如果你想在clone你的代码的时候将代码放到指定的文件夹，比如my-blog文件夹，可以执行以下命令：
$ git clone git@github.com:<你的用户名>/<你的用户名>.github.io.git my-blog

// 打开项目文件夹，与上面两条命令一一对应
$ cd my-hexo-blog
或
$ cd my-blog

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
有的小伙伴可能想在主页写博客,请看[如何搭建自己的hexo博客（上）](https://yangmin4052.github.io/my-hexo-blog/2018/04/20/%E5%A6%82%E4%BD%95%E6%90%AD%E5%BB%BA%E8%87%AA%E5%B7%B1%E7%9A%84hexo%E5%8D%9A%E5%AE%A2%EF%BC%88%E4%B8%8A%EF%BC%89/)。