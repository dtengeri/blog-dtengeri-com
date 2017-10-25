---
title: Compile shared libraries with gcc
layout: post
tags: gcc linux sharedlib
---

Compiling libstest.so:
```bash
gcc -Wall -fPIC -c *.c
gcc -shared -Wl,-soname,libctest.so.1 -o libctest.so.1.0   *.o
ln -sf /opt/lib/libctest.so.1.0 /opt/lib/libctest.so
ln -sf /opt/lib/libctest.so.1.0 /opt/lib/libctest.so.1
```

Using libctest:
```bash
gcc -Wall -L/path/to/lib prog.c -lctest -o prog
```

Running prog:
```bash
export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH
./prog
```