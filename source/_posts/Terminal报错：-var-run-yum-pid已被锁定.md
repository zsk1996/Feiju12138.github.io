---
title: 【踩坑】Terminal报错：/var/run/yum.pid已被锁定
categories:
  - Linux
date: 2020-06-30 21:31:49
---

## 前言

Terminal报错：`/var/run/yum.pid 已被锁定，PID 为 11485 的另一个程序正在运行。`

<!-- more -->

## 解决问题

### 强制结束yum进程

``` sh
rm -f /var/run/yum.pid
```

### 等待一段时间后报错可能会自行消失

### 重启系统

``` sh
reboot
```

## 完成

## 参考文献

[荒原之梦的博客](https://zhaokaifeng.com/?p=1654)

