---
# type: docs 
title: Linux的tee命令
date: 2023-12-25T07:57:47+08:00
description: "介绍一个简单好用的小工具tee，让你的bash神功功力又进一层"
featured: true
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
- bash commands
categories: ["Linux"]
tags: ["Linux", "Bash", "Tips"]
images: ["images/linux.jpg"]
---

对于Linux上面的重定向，大家都很熟悉。例如最常见的用法就是讲一个程序的输出重定向到一个文件里边去。


```
$ ls -la $HOME > /tmp/filelist.txt
```

有时候也需要直接在终端上看到程序的输出。以前我都是傻傻地运行两遍程序，首先运行的时候不做重定向看看输出，然后再运行一次将输出保存到文件。直到有一个看到一个项目中的bash脚本中有个命令 `tee` 很好奇地查了一下才发现了这个小宝贝。

tee这个词语本身就是三通管道的意思，这样说了聪明的你马上就能想到它的作用。跟现实中的三通管类似，它从入口接受输入，然后将接到的内容输出到两个出口。（实际生活的三通管会分流，但是这个tee命令不会哦。）下面看几个例子吧。

```
$ ls -la /home
total 12
drwxr-xr-x  3 root  root  4096  9月  6 21:32 .
drwxr-xr-x 21 root  root  4096 10月 27 21:40 ..
drwxr-x--- 27 bruce bruce 4096 12月 25 07:57 bruce
```

首先我们看到的是 /home文件夹的内容。我们将它通过tee命令输出到终端stdout，同时写到文件中。


```
$ ls -la /home | tee /tmp/filelist.txt
total 12
drwxr-xr-x  3 root  root  4096  9月  6 21:32 .
drwxr-xr-x 21 root  root  4096 10月 27 21:40 ..
drwxr-x--- 27 bruce bruce 4096 12月 25 07:57 bruce

```

接着我们查看写出的文件内容看看是否一致。

```
$ cat /tmp/filelist.txt 
total 12
drwxr-xr-x  3 root  root  4096  9月  6 21:32 .
drwxr-xr-x 21 root  root  4096 10月 27 21:40 ..
drwxr-x--- 27 bruce bruce 4096 12月 25 07:57 bruce
```

是不是很简单很麻利？
这个可爱的小工具还有一个常用的选项 `-a`, 将输出追加到文件中。例如，再次执行命令 `$ ls -la /home | tee -a /tmp/filelist.txt`, 然后查看文件输出。

```
$ cat /tmp/filelist.txt 
total 12
drwxr-xr-x  3 root  root  4096  9月  6 21:32 .
drwxr-xr-x 21 root  root  4096 10月 27 21:40 ..
drwxr-x--- 27 bruce bruce 4096 12月 25 07:57 bruce
total 12
drwxr-xr-x  3 root  root  4096  9月  6 21:32 .
drwxr-xr-x 21 root  root  4096 10月 27 21:40 ..
drwxr-x--- 27 bruce bruce 4096 12月 25 07:57 bruce

```

Tags: Linux, Bash, tee, pipes, redirection
