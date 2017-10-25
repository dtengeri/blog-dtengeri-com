---
title: Replace symbolic links with tar
layout: post
tags: linux symlink tar
---

This is a really slow solution, but works:
```bash
tar -hcf - sourcedir | tar -xf - -C parent_of_newdir
```

Source:

[http://superuser.com/questions/303559/replace-symbolic-links-with-files](http://superuser.com/questions/303559/replace-symbolic-links-with-files)