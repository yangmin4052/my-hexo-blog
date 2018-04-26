---
title: Git Bash中alias的使用
date: 2018-04-25 14:14:04
tags:
---

* 在我们安装完 git 之后，右键会有 Git Bash 命令行工具

* 当你在使用命令行时，有没有发现命令行好长，一不小心就敲错了几个字母？下面教你如何使用 alias 合理装逼

1.  右键打开 Git Bash 命令行工具，并执行用 vim 打开 aliases.sh 文件

```
cd /etc/profile.d/
vim aliases.sh
```

2.  如果你操作过 aliases.sh 此时可能提示你以何种方式打开，我们选择“直接编辑（（E））”（如果你以前没有操作过 aliases.sh 这一步可能不会出现）

3.  此时你已经进入 aliases.sh 文件，点击 i 或者 a 开始编辑，此时左下角会出现“--插入--”或者“--INSERT--”的提示

4.  aliases.sh 文件中已经有两个 alias

```
alias ls='ls -F --color=auto --show-control-chars'
alias ll='ls -l'
```

你可以添加你需要的

```
alias vc='/d/Program\ Files/Microsoft\ VS\ Code/Code.exe'
alias subl='/d/Program\ Files/Sublime\ Text\ 3/sublime\_text.exe'
alias dev='npm run dev'
```

5.  编辑完成之后，点击 Esc，输入:wq，或者点击 Esc 之后，输入两次大写 Z，即保存退出

6.  关闭 Git Bash，重新打开 Git Bash，此时如果你想要在当前文件夹打开 vscode 可以输入

```
vc ./
```

如果你想要在当前文件夹打开 sublime 可以输入

```
subl ./
```

如果你想要在当前文件夹运行开发环境可以输入

```
dev
```

* 注意：vscode 的 terminal 并不能这样使用哦。

* 发挥你的想象力，用好你的 alias。
