---
layout: post
title: "Why another wheel"
image: ''
date: 2019-03-09 22:35:00 +0800
updated: 2019-03-09 22:35 +0800
authors:
- brucejia
tags: 
  - spring

categories:
- Writtings
- Knowlege Base

series:
- notes
---


Why do you invent another wheel? And then throw it away?


#### Rule 0 - Don't invent wheels.

Before the Spring Festival, there came another requirement (from high-high-level decision makers, far-far-away) of resilience of services.
"Resilience" is a golden word for services although this requirement doesn't make too much sense for service D (I don't put the name here if you kill me).

The first conclusion came out the discussion is to support "retry" to external service calls. In sprint planning, the task is only given 2 - 3 points including development,
testing and deployment. While the feature list contains configurable attempts, bakoff policies, jitter support, etc.

Because the schedule is quite tight I don't have enough time to evaluate existing solutions like Netflix or Spring Cloud. So I went on to the wrong way of writing it by myself.
Simply implementing "retry" just for service D is not too touch. I finished it in time. And both QA and I were satisfied with that. Nice!

*This is why I invented another wheel.*

After that I spent more time to look around on Google for existing solutions. I found Spring Retry and Resilience. For Spring Retry I dived into the doc and code and read it through.
It's obviously a better wheel than what I've done in a rush. For example, it uses `Exceptions` in white list for retries while my wheel uses HTTP status code in responses.
And my wheel has to take special care to exceptions. Spring Retry is more easier to use for other projects. But my wheel makes assumptions for the return type of annotated methods.

At this point, although my wheel is not perfect I still want to keep it and enhance it step by step.

Later here comes another requirement to implement `circuit breaker` for our services. This is more chanllenging, to finish in 2 - 3 days.
So I have to seriously think about it. And seriously talk about it to managers. We cannot go further in the wrong way.

*It's time to throw my wheel again. Even I feel sorry about it.*

Last sprint I spent 3 or 4 days to study Spring Cloud, Netflix Hystrix and Resilience. And I delievered a simple evaluation report for the solutions.
And go to the right way.
