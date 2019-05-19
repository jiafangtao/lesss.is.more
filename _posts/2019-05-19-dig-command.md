---
layout: post
title: "Linux Commands - dig"
image: ''
date: 2019-05-19 22:35:00 +0800
updated: 2019-05-19 22:35 +0800
tags: 
  - linux
  - networking
  - dns
description: "dig command used to display dns information"

categories:
- Writtings
- Knowlege Base

series: notes
---

dig (dns information groper)

查询单个主机的信息
$ dig foo.bar.com

结果中的Anwser Section就是该主机的信息，例如IP地址
一下是dig www.qq.com的结果
···
$ dig www.qq.com

; <<>> DiG 9.8.3-P1 <<>> www.qq.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21106
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.qq.com.			IN	A

;; ANSWER SECTION:
www.qq.com.		300	IN	CNAME	https.qq.com.
https.qq.com.		300	IN	A	61.129.7.47

;; Query time: 11 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun May 19 22:47:08 2019
;; MSG SIZE  rcvd: 64
···

可以看出来www.qq.com是一个CNAME。它实际上指向了https.qq.com.这个域，而它的ip是61.129.7.47。你
可以试着在浏览器中输入https://61.129.7.47/看看是什么结果。
···
···
