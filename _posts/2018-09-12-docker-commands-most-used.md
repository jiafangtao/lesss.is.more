---
layout: post
title: "Docker常用命令"
image: ''
date: 2018-09-12 09:45:00 +0800
tags: 
  - docker  
description: "整理总结一些常用的docker命令"

categories:
- Writtings
- Programming

series: notes
---

### 通用指南 (docker commands in general)

### docker build

Build a docker image from Dockfile. If no file name is specified, it will build from ```./Dockerfile```.

### docker run

Run a docker container from an image. Most used options are:

- --interactive, -i       Run the container in ```interactive``` mode
- -t                      Run the container with a terminal (allocate a psudo-TTY)
- --name                  Name the container
- --env                   Set environment variables to the container. This is a very important way to differenciate running environment for containers. For example, in CloudOS, environment variables are defined in ADF files and then applied as environment variables to the containers.

### docker inspect

### docker attach

Attach to the container's STDIN, STDOUT and STDERR. This is very useful to do trouble-shooting or monitoring when the container was launched in background mode, i.e. detached mode.

### docker ps

### docker images

### docker rename

### docker rmi

