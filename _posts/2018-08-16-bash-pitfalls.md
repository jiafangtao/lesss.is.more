---
layout: post
title: "Bash的坑"
image: ''
date: 2018-08-16 10:30:00 +0800
tags: bash
description: "Bash是门应用广泛的编程语言，然而跟严肃的高级语言相比存在很多的坑。这篇博文专门记录我在工作中犯过的各种错"
categories:
- Writtings
- Programming
series: making progress
---

### Bash的坑

坑之一：变量赋值

*错误的写法：*
```
myvar = "hello, world"
```

*正确的写法：*
```
myvar="hello, world"
```
*原因：*
等号左右不能有空格

坑之二：判等

坑之三：

