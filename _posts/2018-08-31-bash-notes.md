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
      
当`command`被提供是，这个`command`会替代当前的shell, 而不创建新的进程。如果没有指定执行的命令，重定向会被用来影响当前的shell环境。
(BJ: 不明白这一段的意思，囧)

要从命令行运行一个可执行文件或一个Shell脚本，通常根本就不需要用到`exec`, 更常见的做法是用“./”后面接要执行的可执行文件或脚本，例如 `./hello.out`
如果没有加上“./”前缀，Bash只会搜索出现在环境变量`path`中的路径（这个路径常常包含了`/bin`, `/usr/local/bin`等等），而不是搜索当前工作文件夹。

既然可以简单明了地执行一个程序或者脚本，那么问题来了：

Q: 我们为什么需要`exec`呢？
A: TODO

### $@

### env
