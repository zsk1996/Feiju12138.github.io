---
title: 【踩坑】Homebrew报错：Another active Homebrew
categories:
  - MacOS
date: 2020-09-11 08:45:41
---

## 前言

Homebrew报错：`Another active Homebrew update process is already in progress.`

<!-- more -->

## 原因

- 手动终止了brew update相关命令

## 解决问题

- 删除锁文件

``` sh
rm -rf /usr/local/var/homebrew/locks
```

## 完成

## 参考文献

[CSDN——w8ed](https://blog.csdn.net/MASILEJFOAISEGJIAE/article/details/85253919)

