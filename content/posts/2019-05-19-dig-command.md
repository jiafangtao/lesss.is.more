---
layout: post
title: "Linux Commands - dig"
image: ''
date: 2019-05-19 22:35:00 +0800
updated: 2019-05-19 22:35 +0800
authors:
- brucejia
tags: 
  - linux
  - networking
  - dns
description: "dig command used to display dns information"

categories:
- Writtings
- Knowlege Base

series:
- notes
---

dig (dns information groper)

### 查询单个主机的信息
$ dig foo.bar.com

结果中的Anwser Section就是该主机的信息，例如IP地址
一下是dig www.qq.com的结果

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


可以看出来www.qq.com是一个CNAME。它实际上指向了https.qq.com.这个域，而它的ip是61.129.7.47。你
可以试着在浏览器中输入https://61.129.7.47/看看是什么结果。

### 查询主机的CNAME
$ dig www.sina.com CNAME

得到的结果片段如下

;; QUESTION SECTION:

;www.sina.com.			IN	CNAME

;; ANSWER SECTION:

www.sina.com.		300	IN	CNAME	us.sina.com.cn.


### 从指定的服务器查询DNS信息
上面的查询都没有指定特定的DNS服务器，有时候本地的DNS服务器可能不是很准确，这样我们需要去查询权威一点的服务器，例如谷歌，godaddy或国内的dnspod。

$ dig @target-dns.com foo.bar.com

命令中在@的后面加上DNS服务器的地址即可。


### 反向查询某个DNS服务器

$ dig -x 8.8.8.8

; <<>> DiG 9.8.3-P1 <<>> -x 8.8.8.8
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53894
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:

;8.8.8.8.in-addr.arpa.		IN	PTR

;; ANSWER SECTION:

8.8.8.8.in-addr.arpa.	1044	IN	PTR	google-public-dns-a.google.com.



【参考】学习过程中参考了man page - dig 以及部分例如https://www.imooc.com/article/26971?block_id=tuijian_wz 

<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="https://rcm-cn.amazon-adsystem.com/e/cm?ref=tf_til&t=brucejia_blog-23&m=amazon&o=28&p=8&l=as1&IS2=1&asins=B079GKJY5N&linkId=7e5a5ff5acf1fbdec8b329f6ab4deec2&bc1=FFFFFF&lt1=_blank&fc1=333333&lc1=0066C0&bg1=FFFFFF&f=ifr">
    </iframe>
    
