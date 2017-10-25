---
title: Recursively remove .svn directories
layout: post
tags: linux find rm
---

Recursively remove .svn directories:
```bash
rm -rf `find . -type d -name .svn` 
```

More info:
[http://www.ossramblings.com/remove_svn_recursively](http://www.ossramblings.com/remove_svn_recursively)