---
# type: docs 
layout: post
title: "如何阻止或禁止WebSocket"
date: 2023-12-24 19:30:00+08:00
authors:
- brucejia
carousel: false
draft: false
featured: true
tags: 
  - websocket
  - tips
toc: true
description: "模拟WebSocket被阻止的情况"
categories: "小技巧"
images: []
---

前一个项目中使用了WebSocket技术来实现前端和后端的消息及时通知，具体有几种类型的消息，包括其中非常重要的一点就是后端计算的过程可能比较长，一些输出到stdout和stderr的信息需要让前端展示。前后端都是用了socket.io库，而transport选择了websocket。一次技术讨论的时候，大家提到了说有的客户网络环境中可能会禁用WebSocket，那样我们的前后端无法正常通信了，这是一个很大的技术风险。我记得socket.io是支持websockets和long polling两种传输方式的，如果万一真的websocket被阻断了，那么我们可以手动甚至自动降级到long polling。口说无凭，show me the code，我就做一些实验来看看技术方案的可行性。

首先考虑的一点就是在客户环境中如何禁止websocket。因为websocket本身是通过http协议upgrade来的，它和普通的HTTP通信使用相同的端口，所以采用封端口的方式肯定是不行的。那么，通过应用层也就是HTTP通信层来做，应该是靠谱的。接下来我考虑的是，如何模拟这种对websocket的封锁呢？

马上能够想到的方案是用一个代理服务器，例如nginx, 配置特定的规则对于websocket的upgrade请求拒绝掉或者返回502之类的错误码。但是我不清楚ng里边如何配置这样，也许需要自己写一个module, 掂量一下想想杀鸡不能用牛刀，以后再来研究这个。说到代理服务器，其实Fiddler的工作方式也是代理服务器，而Fiddler是可以通过简单的脚本来对HTTP requests/responses做一些处理的。于是马上下载了Fiddler Classic, 打开它的Rules尝试一番。

对于实验的目标网站，可以是自己的项目或者是这个小可爱 https://echo.websocket.org/.ws 这个网站实现了一个简单的echo服务，客户端也会每隔一秒给服务器发送一条消息，你也可以让客户端停止发送消息。

打开Fiddler Classic的菜单项`Rules` --> `Customize Rules...`, 找到代码中 `OnWebSocketMessage` 函数，如下图所示修改并且保存。

![fiddler-code-block-ws](fiddler-1.png#center)

再次打开Rules菜单后发现，我们刚刚添加的规则已经出现在自定义规则中了。

![fiddler-ui-rules-block-ws](feature.png#center)


勾选它然后实际测试下，如下图是我使用https://echo.websocket.org/.ws 做测试的截图。


![echo-server](ws-blocked.png#center)

结合项目代码实际效果见下图。

![fiddler-ui-show-ws](fiddler-0.png#center)


**另外的思路**

1. 网上有人提出来可以在客户端初始化的时候，用一行简单代码
 
 ```window.websocket = undefined;```

 暴力禁止websocket的使用。我不打算用这样的方式，原因有多个。其一、需要修改代码所以这个方法是侵入式的，与客户现场所遇到的情况不符合；其二、这会造成现有代码的逻辑错误，很可能会影响其他部分的代码。所以这不是一种很干净的做法，毒副作用强烈。当然，我建议看官们根据自己的具体情况酌情服用。

2. 上面我的做法是调用`Abort()`终止了请求的处理，还有一种做法是返回`502`。这个方法我没有试过，留给看官们自行研究吧。


**写在最后**

当然也给自己留点作业，还需要继续研究`socket.io`是否能够`gracefully downgrade to long polling`.


TAGS: websocket, web开发, fiddler, socketio

