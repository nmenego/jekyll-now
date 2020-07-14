---
layout: post
title: Git Empty Commit
tags: tech
---

Yesterday (2020/07/13), Github had a 5-hour-ish [outage](https://www.cbronline.com/news/github-outage-impacts-millions-of-developers-issue-found-fix-coming). Naturally, this caused a lot of frustrations for developers using the platform. I noticed the problem when certain changes I pushed to my Github branch was missing. Frustrating refreshes did not do the trick. This was important as our pipelines are programmed to create the artifacts, and release them to our staging environment. Otherwise, we'd have to do it manually, which was a pain.

Decided to wait it out, and see if Github recovers in several hours while working on other stuff. When Github recovered after 5-hours or so, I saw that my pushes were not reflected at all! So I wanted to bump my remote branch, just to trigger the pipeline. Saw this command from the interwebs:

```
> git commit --allow-empty -m "empty commit to trigger pipeline"
```

Just what I needed! No more modifying the README just to add arbitrary spaces!
