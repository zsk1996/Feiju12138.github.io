---
title: 【踩坑】Linux 报错 "Read-only file system"
categories:
  - Linux
date: 2020-01-14 20:42:23
---

## 前言

`Linux`报错`Read-only file system`，是因为进入文件系统的只读模式，通过`root`用户修改系统配置文件即可解决问题

<!-- more -->

## 解决问题

``` sh
mount -o remount rw /
rm -rf /etc/.pwd.lock
```

## 完成

## 参考文献

[CSDN——Aidon-东哥博客](https://blog.csdn.net/u010839779/article/details/77062347)

