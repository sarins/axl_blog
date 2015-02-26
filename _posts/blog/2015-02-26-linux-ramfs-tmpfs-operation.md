---
layout: post
category: blog
categories: blog
title: Linux ramfs/tmpfs 基本操作
author: Axl Zhao
tags: [linux, ramfs, create ramfs, tmpfs, create tmpfs]
published: true
sticky: false
---

# Linux ramfs/tmpfs 基本操作

##### 挂载ramfs

```
# 基于root权限操作，建立挂载点。
[root@MMPC ~]# mkdir -p /mnt/test_ramfs

# 挂载ramfs。
[root@MMPC ~]# sudo mount -t ramfs -o size=32m ramfs /mnt/test_ramfs

```

- - -

##### 挂载tmpfs

```
# 基于root权限操作，建立挂载点。
[root@MMPC ~]# mkdir -p /mnt/test_tmpfs

# 挂载tmpfs。
[root@MMPC ~]# sudo mount -t tmpfs -o size=32m tmpfs /mnt/test_tmpfs

```

- - -

##### 特性对比

| 特性 | ramfs | tmpfs |
|--------|--------|--------|
| 固定大小 | No | Yes |
| 使用Swap | No | Yes |
| 持久存储 | No | No |

