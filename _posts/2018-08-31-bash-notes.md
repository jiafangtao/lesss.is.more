---
layout: post
title: "Linux Bash笔记"
image: ''
date: 2018-08-31 15:35:00 +0800
tags: 
  - linux 
  - bash 
  - shell programming
description: "整理总结一些常常用到的Linux命令和Bash编程的知识"

categories:
- Writtings
- Debugging
- Programming

series: notes
---

### bash -c ''

### exec
`exec` 是Bash的一个内置命令，用于执行一个命令或脚本。
参考：https://ss64.com/bash/exec.html

语法
      exec [-cl] [-a name] [command [arguments]]

选项
      -l   Place a dash at the beginning of the zeroth arg passed to command.
           (This is what the login program does.)

      -c   Causes command to be executed with an empty environment.

      -a   The shell passes name as the zeroth argument to command.
      
当`command`被提供时，这个`command`会替代当前的shell, 而不创建新的进程。如果没有指定执行的命令，重定向会被用来影响当前的shell环境。
(BJ: 不明白这一段的意思，囧)

要从命令行运行一个可执行文件或一个Shell脚本，通常根本就不需要用到`exec`, 更常见的做法是用“./”后面接要执行的可执行文件或脚本，例如 `./hello.out`
如果没有加上“./”前缀，Bash只会搜索出现在环境变量`path`中的路径（这个路径常常包含了`/bin`, `/usr/local/bin`等等），而不是搜索当前工作文件夹。

既然可以简单明了地执行一个程序或者脚本，那么问题来了：

Q: 我们为什么需要`exec`呢？
A: TODO

### $@

### env
显示当前所有的环境变量，跟Windows上的SET命令是一样的。例如查看某个环境变量
```env | grep AWS_REGION```

### test

计算(评估)表达式的值，如果表达式返回true则这个命令返回0，否则返回1。
语法：
  ```test expression```

中括号[是test的别名，在脚本中常常见到。语法如下：

```[ expression ]```

例如：

```[ -d /usr/local/tomcat/ ]``` 检查tomcat文件夹

This is the most useful post about *.bashrc* and *.bash_profile*

[http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html)

Personal bash aliases to save a lot of keyboard hits
#
# aliases for docker-compose
#
alias dcbuild='docker-compose build'
alias dcup='docker-compose up'
alias dcdown='docker-compose down'
alias dcps='docker-compose ps'
alias dcexec='docker-compose exec'

#
# aliases for git
#
alias gs='git status'
alias gc='git commit'
alias gp='git push'
alias gb='git branch'
alias gco='git checkout'
alias gl='git log'

