---
title: Git on Dropbox in 5 commands
layout: post
tags: git dropbox
---

Create git repository:
```bash
cd ~/Dropbox
mkdir -p git/repo.git
cd git/repo.git
git --bare init
```

Clone: 
```bash
git clone file:///home/user/Dropbox/git/repo.git
```

Source:
[http://tumblr.intranation.com/post/766290743/using-dropbox-git-repository](http://tumblr.intranation.com/post/766290743/using-dropbox-git-repository)