---
layout: post
title: "Docker常用命令"
image: ''
date: 2018-09-12 09:45:00 +0800
updated: 2019-04-03 16:00:00 +0800
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

Show low-level details of containers, specified by id or name.

### docker attach

Attach to the container's STDIN, STDOUT and STDERR. This is very useful to do trouble-shooting or monitoring when the container was launched in background mode, i.e. detached mode.

### docker ps

Just like Linux `ps` command, this lists all running containers.

### docker images

List all docker images available on this machine.

### docker rename
Rename a docker container to a new name

### docker rmi

Remove a docker image


## docker compose commands

### docker-compose up
Start up the services defined in the default configuration file, which is docker-compose.yml

### docker-compose down
Stop all services which were brought up previous by a `docker-compose up` command. It will delete the containers after stop them. The docker network created will also be destroyed gracefully.

Other than `docker-compose down`, if you hit `ctrl-c` the containers will be stopped while not deleted. And the docker network will remain there. So it's recommended to use this command to take the services down gracefully.

### docker-compose exec
This is identical to `docker exec`. You can execute a command in a selected service.
