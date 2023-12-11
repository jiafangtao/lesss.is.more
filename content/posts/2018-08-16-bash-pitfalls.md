---
layout: post
title: "Bash的坑"
image: ''
date: 2018-08-16 10:30:00 +0800
tags: 
- bash
description: "Bash是门应用广泛的编程语言，然而跟严肃的高级语言相比存在很多的坑。这篇博文专门记录我在工作中犯过的各种错"
categories:
- Writtings
- Programming
series: 
- making progress
---

### Bash的坑

Bash是门应用广泛的编程语言，然而跟严肃的高级语言相比存在很多的坑。这篇博文专门记录我在工作中犯过的各种错

坑之一：变量赋值 (Assignment)

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

CURRPATH=/usr/bin/node

*错误的写法*
```
if [ "$CURRPATH" -eq "/usr/bin/node" ]; then
    # do something here
fi
```

*正确的写法*

```
if [ "$CURRPATH" = "/usr/bin/node" ]; then
    # do something here
fi
```

*原因*

Bash会报错，大概是说 \[: integer expression expected”.
这是因为-eq是用来比较整型的，而不是比较字符串。字符串的比较使用等号(=)就可以了。



坑之三： 中括号后面的空格

https://unix.stackexchange.com/questions/99185/what-do-square-brackets-mean-without-the-if-on-the-left

坑之四： $?

$?是上一条命令的返回值，例如上一个执行 程序的退出代码(exit code)

echo $myvar

简单的一个echo也会影响到$?的值。

function onErr (msg) {

}

