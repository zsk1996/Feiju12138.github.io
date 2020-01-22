---
title: 【踩坑】Mac报错"Read-only file system"
categories:
  - MacOS
date: 2020-01-17 09:49:06
---

## 前言

Mac使用`mkdir: /sw`命令在系统根目录新建目录时，报错"Read-only file system"。

<!-- more -->

## 解决方法

### 关闭 SIP 系统完整性保护

[传送门](https://feiju12138.github.io/2020/01/17/系统完整性保护)

### 挂载读写权限

``` sh
mount -o remount -w
```

## 完成

## 参考文献

[V2EX——shmilwdc](https://www.v2ex.com/t/607330)

