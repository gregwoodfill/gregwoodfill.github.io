---
layout: post
title: "Speeding up git-svn"
date: "2017-04-01 18:58:00 -0500"
---
Git-svn has been an essential part of my workflow for about a year since I last worked on a pure fit project. Using it on a huge monolithic repo can be unbearably slow on the initial clone and subsequent fetches

Running

```
git fetch|clone --log-window-size=1000
```

will cause git to fetch svn commits of blocks of 1000 instead of the default 100. You can specify to your liking, though it may cause heap or timeout issues if set too large.
