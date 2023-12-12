---
# type: docs 
title: Cheat Sheet for Git Credential Commands
date: 2023-12-12T08:44:47+08:00
authors: brucejia
featured: false
draft: true
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
categories: ["tools", "programming"]
tags: ["git", "cheatsheet"]
images: []
---

Git is a lightweight tool which is mainly used to track versions of your source code (or other text-based files.) When working with a git server, you are always prompted to input your username and password (PAT, i.e. Personal Access Token, is a better way than main password.) again and again. 

To save your time, git offers some credential helpers which are quite nice. Open a terminal and run such a (shell) **command**

`$ git help -a | grep credent`


You will get similiar output like below.

```
   credential           Retrieve and store user credentials
   credential-cache     Helper to temporarily store passwords in memory
   credential-store     Helper to store credentials on disk

```




<!--more-->

Content.
