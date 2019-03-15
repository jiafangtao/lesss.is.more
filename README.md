# This is a weblog using Jekyll



### Preview it lively online:

[http://www.brucejia.net/](http://www.brucejia.net/)


### Build it locally on your box ###

- Shortcuts: run `start.sh` or `npm run serve`



- Or (under the hood) navigate into the root directory of your local Jekyll site repository.

Run your Jekyll site locally:

```bundle exec jekyll serve```

Configuration file: /Users/octocat/my-site/_config.yml
           Source: /Users/octocat/my-site
      Destination: /Users/octocat/my-site/_site
Incremental build: disabled. Enable with --incremental
     Generating...
                   done in 0.309 seconds.
Auto-regeneration: enabled for '/Users/octocat/my-site'
Configuration file: /Users/octocat/my-site/_config.yml
   Server address: http://127.0.0.1:4000/
 
 Server running... press `ctrl-c` to stop.

- Preview it locally

[http://localhost:4000](http://localhost:4000)


### Github Markdown Reference ###
[mastering-markdown](https://guides.github.com/features/mastering-markdown/)

## How to create a post ? 

_posts create a file .md with structure:

```md
---
layout: post
title: "Lorem ipsum speak.."
date: 2016-09-13 01:00:00
image: '/assets/img/post-image.png'
description: 'about tech'
tags:
- lorem
- tech 
categories:
- Lorem ipsum
twitter_text: 'How to speak with Lorem'
---
```
