---
title: Clean up old remote branches in GIT
layout: post
tags: git
---

List what would be deleted:  
`git remote prune origin --dry-run`  
Do the clean up:  
`git remote prune origin`