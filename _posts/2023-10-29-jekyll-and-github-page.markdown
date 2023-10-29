---
layout: single
title:  "Building a blog site with Jekyll and GitHub Page"
date:   2023-10-29 13:00:00 -0700
categories: software
---
I have been thinking of building my website for a while, though I was always blocked by my hesitation and uncertainty - how does it work? How will the DB schema look like, what backend API should it support, how should I make sure that only I have the credentials to update the website, etc?

While it turns out that I was simply overthinking it. Yesterday, after being a bit burnout from other things, I thought "F**k it, I am gonna do it even though I don't know how right now". Therefore, if you are reading this article, the chances are I have built my site and it is still running. 

Anyway, this blog is about how I built my first personal website, probably this could be helpful to you.

The site itself is hosted on [Github Page](https://pages.github.com/), a project that allows you to host **static content** from a GitHub repository, so Github will take care of all the credentials things - only the repo owner can update the website. In terms of the commenting feature, I am still figuring it out (TBD).

You could technically build all static content (HTML, CSS, JS) from scratch, or use some advanced framework ([React](https://github.com/gitname/react-gh-pages)), though I choose something in between - [Jekyll](https://jekyllrb.com/), which in my understanding is a static content generator and organizer. Although to be honest, the determining reason is that it is kinda officially supported by GitHub Pages, according to this doc - [Setting up a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll).

For Linux and Windows users, I believe following the doc should be sufficient. However, for macOS users, please be prepared to spend some time figuring out Ruby versions. When I tried to follow the doc on my Macbook, I found that in order for Jekyll to work, I have to update my Ruby, but no matter how hard I try, my laptop won't let me (yes, I tried both "sudo" and "su"). Later on, I figured that a native Ruby is coming with the MacOS located at "/user/bin", and no one is allowed to update it (probably there is some system-level code that relies on that version of Ruby). Luckily, I found this [Stackoverflow post](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma) suggesting that MacOS users should install a separate Ruby apart from the one that comes with the system. I tried, and I have to admit, "ruby-install" and "chruby" works like a charm. 

After addressing the ruby version problem, it should be pretty straightforward to build and deploy the site and see the result. If you want your site to look a bit nicer, I would suggest searching for some Jekyll themes, as it seems there is a large Jekyll community I didn't know before. FYI, I use [minimal mistakes](https://mmistakes.github.io/minimal-mistakes/).

While, this is my first blog on my first site, so I cannot help talking a bit too much. Appreciate it if you finish the reading. For my next step, I think I am going to figure out how the commenting feature works in this static site, as I believe I saw some posts about it when I tried to hunt the theme for my site. See u soon. 