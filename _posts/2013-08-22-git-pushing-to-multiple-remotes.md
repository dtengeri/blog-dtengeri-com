---
title: "Git: pushing to multiple remotes"
layout: post
tags: git
---

1. Get the actual push remote with:  
   `git remote -v`
1. Add the new remote with:  
   `git remote set-url --add --push origin git://another/repo.git`
1. Because of a bug in git (1.8.x) you have to add the original remote again:  
   `git remote set-url --add --push origin git://original/repo.git`
