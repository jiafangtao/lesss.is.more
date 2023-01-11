---
layout: post
title: "Mediation on FD Type System"
date: 2023-01-11 20:34:00
tags: 
  - notes
  - type system
description: "支持FD通用数据规范时的所思所想"
categories:
- Writtings
- Essay
- Thoughts
series: "notes"
---

Personal Note - FD Type System



Type System
===========
FD data schema定义的远远不是一套schema, 从propertyset为基础出发，FD定义的是一套运行时类型系统。虽然它的重点在于定义数据，但是也包含了元数据的定义，以及数据的关联和约束。

我们可以与常规的编程语言相比，来理解我们所说的类型系统。对于编译型强类型语言例如C/C++，所有的类型在编译时确定，在运行时已经不存在或很少存在类型信息（RTTI除外）。C/C++程序之所以能够运行，其根基在于地址和偏移量，或者合而言之就是地址 - 数据的地址或操作的地址，这也是现代计算机的根本所在。

更加现代化的语言例如JAVA或Python，因为有语言内建的Reflection特性等，它们有着完整的运行时类型系统 - 在任何时候一个对象是什么类型，可以执行什么操作都是确定的。当然这些语言的强大特性是和额外的开销伴生的：占用更多的内存空间，使用更多的CPU资源。

说回到FD，为什么我们需要一套类型系统？我们需要什么样的类型系统？我们该如何实现这套类型系统？
FD的mission是建立一套标准化的可以扩展的数据规范。各个产品product/service，包括第三方开发的，都能够在这套数据规范的框架内实现互通和协作。（引申一下general search要解决什么问题？如果没有一套确定的类型系统作为基础general search可以做吗？能够做到足够通用吗？如何做到呢）

该数据规范使用JSON或XML来描述；

数据类型的定义存储与Forge Schema Service中，或者使用embeded的形式跟数据一起提供；

原子类型和自定义类型

组合方式和继承方式

Topic: 数据可交换
交换双方都能够解读对方的数据 - 因为双方用同一套方案描述和呈现数据；统一的内建数据型别(Primitive Types)， 相同的扩展方式（组合和继承）

Topic: 快照和delta
大多数时候我们希望看到的是系统的一个快照，但有时候人们感兴趣的是delta，也就是在revision之间的变化，或者说两个关联快照之间的变化。快照和delta这两个概念本身并不属于类型系统，它们属于应用。例如ECS架构中，并没有snapshots或者revisions，但是具体应用可以将它们定义为特定的entities。

Topic: 语法层次和语义层次

Topic: 语言和惯用法

“语言”在语法语义层次上提供了building blocks，具体的应用例如AIM Data选取合适的子集，加上自己扩展的blocks来构建自己特定系统或产品。

思想走得再远也需要回归到行动的种子，那么Search要做什么？

从上面我们所认识到的部分，Forge Data schema能够表述的是ECS中的entities和components，那么另外很大一个部分就是system - Search的角色就是一个system。system根据输入的数据决定自己的行为，行为可能产生新的数据或对现有数据进行更新。

相对于其他的system来说，Search是一个相对简单的system。它需要消费数据，但是并不改变数据。它产生的索引文件等本身是在FD之外的。
