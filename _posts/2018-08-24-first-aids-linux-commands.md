---
layout: post
title: "devops急救手册之常用的Linux命令"
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

`# Show total file size of current directory`
```
  $ du -sh .
```


