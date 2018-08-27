# This site is using theme "Space Jekyll"

A simple and elegant Jekyll theme based on Spacemacs. The theme works well on mobile devices as well.

See a live demo [here](https://victorvoid.github.io/space-jekyll-template/).

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

And preview it here:

http://www.brucejia.net/


### Build your local Jekyll site ###

*Tips: I added a script `start.sh` to save my time and memory as I'm not good at remember command like below.*


Navigate into the root directory of your local Jekyll site repository.

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

Preview your local Jekyll site in your web browser at http://localhost:4000.


### Github Markdown Reference ###
[mastering-markdown](https://guides.github.com/features/mastering-markdown/)
