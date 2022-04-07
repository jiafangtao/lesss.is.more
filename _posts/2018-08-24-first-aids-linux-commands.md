---
layout: post
title: "急救手册之常用Linux命令"
image: ''
date: 2018-08-24 15:40:00 +0800
tags: 
  - linux 
  - devops 
  - shell commands
description: "需要在线上调试程序或查找问题的码农同学们，是不是经常想用一些Linux命令却记不清，看man pages或google又嫌太费时间？这个帖子就是你的急效救心丸"

categories:
- Writtings
- Debugging
- 
series: notes
---

### Linux Commands for Devs who are acting Ops 

#### `find` command
```
  在当前文件夹及子文件夹中（递归）查找所有以lock结尾的Python文件
  $ find . -type file -name "*lock.py"
  
  在当前文件夹中查找所有Python文件（不查找子文件夹）
  $ find . -type file -depth 1 -name "*.py"
  
  在多个文件夹中查找所有shell文件
  $ find ./folder1 ./folder2 -name "*.sh"
  
  在当前文件夹下查找5分钟之内被修改的文件，并排序
  $ find -s . -ctime -5m
```

#### `uptime` command

```
  $ uptime --since
```

#### `top` command

```
  $ top -p <pid>
```
```
  $ top -p <pid> -H
```

#### `ps` commmand

```
  $ ps aux
```
```
  $ ps el
```  

#### `tail` command

#### `du` command


```
  # Show total file size of current directory
  $ du -sh .
```

### `lsof` command

