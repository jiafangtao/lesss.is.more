---
layout: post
title: "关于代码可读性的一些絮絮叨叨"
image: ''
date: 2019-08-20 13:15:00 +0800
updated: 2019-08-21 12:17 +0800
tags: 
  - programming
  - unit testing
  - refactory
  - 重构
  - 单元测试的艺术

description: "可读性是代码第一要求"

categories:
- Writtings
- Essay
- Thoughts

series: notes
---
一些小事的絮絮叨叨

程序员的日常，要花大量时间跟代码打交道：写代码，改代码，读代码。而其中占用最多时间的是读代码，读自己的代码，同事的代码，同产品的或者其他产品的，有时候也需要读懂第三方库和框架的代码。跟很多同事一样，我也觉得写代码的难度远远比不上读懂别人的代码，很多情况下是因为代码可读性很差。

代码可读性这个属性，不是很容易度量，所以没有什么自动化工具来帮助我们。然而，作为一个合格的程序员，良好的可读性依然是我们应该追求的目标。我之所以想到这个问题，主要是因为从去年秋天开始我有机会重新审视和修改以前完成的一个项目，因为主要任务是移植到新的环境，而功能方面并没有很多修改，所以整个过程中我有时间来思考代码的可读性, 可维护性, 以及设计的好坏这些非功能性指标。

D项目是2016年底开始开发的，那个时候基本节奏就是赶进度啊赶进度。代码一点点堆积起来，缺啥补啥。可想而知，慢慢地代码就腐朽不堪也无可奈何。因为设计的不好，单元测试也不好做。（别问我们为什么不搞TDD！！！我们都是面向sprint编程的）后来项目做完，还算挺稳定的，就跟没有机会找老板要时间去做重构或者改单元测试了。去年秋天，机会终于来临。我可以有自由支配的时间来完成那些“边边角角”的事情。当然，这里边很多时间都是在做user story里夹带“私货”的方式做的，例如改一个功能的时候顺手把相关的代码重构一下。几个月的时间里，我也趁机读了好几本书，例如[《设计模式》](http://union.dangdang.com/transfer.php?sys_id=1&ad_type=10&from=P-314444&backurl=http%3A%2F%2Fproduct.dangdang.com%2Fproduct.aspx%3Fproduct_id%3D27875838)和[《重构》](http://union.dangdang.com/transfer.php?sys_id=1&ad_type=10&from=P-314444&backurl=http%3A%2F%2Fproduct.dangdang.com%2Fproduct.aspx%3Fproduct_id%3D27851757)，这两本书都是重读，有常读常新的感觉。新的书主要是讲JUnit和Mockito的电子书，名字记不清了。还有一本是[《单元测试的艺术》](http://union.dangdang.com/transfer.php?sys_id=1&ad_type=10&from=P-314444&backurl=http%3A%2F%2Fproduct.dangdang.com%2Fproduct.aspx%3Fproduct_id%3D23532623)，有部分章节读来也是颇有裨益的。


书籍是人类进步的阶梯

 {% include book-refactory.html %}
 {% include book-design-patterns.html %}
 
 {% book-art-of-unit-testing.html %}

Tags: #单元测试 #单元测试的艺术 #重构 #设计模式
