---
title: 【踩坑】CentOS Parallels Tools 安装失败
categories:
  - 虚拟机
date: 2020-01-31 15:56:19
---

## 前言

在`CentOS`下安装`Parallels Tools`失败

<!-- more -->

## 准备工作

- [kernel-devel-2.6.32-754.27.1.el6.x86_64.rpm](http://mirror.ihep.ac.cn/cern/slc64/x86_64/yum/updates/repoview/kernel-devel.html)

## 原因

- 由于手动安装`Linux`，缺少`kernel-devel.rpm`软件

## 问题解决

- 安装`kernel-devel.rpm`

``` sh
rpm －i kernel-devel-2.6.32-754.27.1.el6.x86_64.rpm
```

## 完成

## 参考文献

[CSDN——yxdydSky](https://blog.csdn.net/yxdayd/article/details/48229415)

