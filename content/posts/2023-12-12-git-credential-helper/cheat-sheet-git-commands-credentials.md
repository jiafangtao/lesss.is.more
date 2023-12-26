---
# type: docs 
title: Cheat Sheet for Git Credential Commands
date: 2023-12-12T08:44:47+08:00
authors: brucejia
description:
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: true
series:
categories: ["tools", "programming"]
tags: ["git", "cheatsheet"]
images: ["images/git-logo.png"]
---

Git credential helpers can save you a lot of time to avoid repeatively type in your username and password again and again.

<!--more-->
Git is a lightweight tool which is mainly used to track versions of your source code (or other text-based files.) 

<!--more-->

When working with a git server, you are always prompted to input your username and password (PAT, i.e. Personal Access Token, is a better way than main password.) again and again. 

To save your time, git offers some credential helpers which are quite nice. Open a terminal and run such a (shell) **command**

`$ git help -a | grep credent`


You will get similiar output like below.

```
   credential           Retrieve and store user credentials
   credential-cache     Helper to temporarily store passwords in memory
   credential-store     Helper to store credentials on disk

```

Depends on your installation, you may see more for this part, for example, you may have some GUI tools to help you manage the credentials. The built-in two helpers are `credential-cache` and `credential-store` which may be enough for daily usage for most of the typical cases.

`credential-cache` helper, as the name indicates, it's simply a cache of user's username and password. When it's invoked, git keeps the user's username and password in **memory** for a while and during that short period git will not prompt the user to enter username and password again and again. With my installation on Windows, when I run below command to tell git to use this helper, git will keep a short memory `about 15 minutes`.

```$ git config credential.helper cache```


Another choice is `credential-store`, which stores the user credentials to a file. Normally if not otherwise specified it's `$HOME/.git-credentials`. As this file contains sensitive data, be sure to never expose it.

```$ git config credential.helper store```

<!--more-->

Tags: git, credentials
