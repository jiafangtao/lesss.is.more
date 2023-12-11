---
layout: post
title: "golang中的channel和routine"
date: 2022-12-20 14:44:00
tags: 
  - golang
  - gorountine
  - channel
description: "好玩的go语言"
categories: "golang"
series:
- "Programming Languages"
---
 
 
### 初次体验golang中的rountine和channel

先看看下面的代码。其中reader函数是作为gorountine执行的，它从channel中反复读取一个整数并打印。主函数main启动reader之后执行循环将1-20逐个写入channel。


```
package main

import "fmt"

func main() {
	c := make(chan int)
	go reader(c)

	i := 1
	for i <= 20 {
		c <- i
		i++
	}
}

func reader(c chan int) {
	for {
		x := <-c
		fmt.Println("Read from channel, got ", x)
	}
}

```

注意这里的channel不带有缓冲，是阻塞的。上面的代码能够正常运行。这是因为虽然channel是阻塞的，但是reader这个gorountine会从channel读取，所以不会造成deadlock。
如果将将main函数改成这样，会造成死锁。

```
  i := 1
	for i <= 20 {
		c <- i
		i++
	}

	go reader(c)
```

运行时的结果类似这样

```
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [chan send]:
main.main()
	/Users/foo/test6.go:11 +0x44
```

如果我们将channel更改成带有缓冲区的类型呢？

```
func main() {
	c := make(chan int, 20)

	i := 1
	for i <= 20 {
		c <- i
		i++
	}
  
	go reader(c)
```

如上我们设置缓冲区大小为20，刚好能够容纳1-20的测试数据。运行程序不会再报错。这里读者可以猜猜看如果缓冲区设置成小于20呢？读者自己试试看。
另外一个问题是虽然代码运行不会报错，但是我们看不到任何输出，因为main在reader还没有执行就结束了，聪明的读者，想想看如何解决这个问题？

通过上面的简单例子，你应该能够弄明白channel的阻塞，缓冲区的概念了吧！
