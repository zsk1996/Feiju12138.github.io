---
title: 【笔记】tar命令压缩与解压
date: 2019-11-13 23:57:08
tags:
---

## 前言

在 Linux 系统下，最常用的打包命令就是 tar 了，本篇文章介绍一下最基本的压缩与解压命令。

<!-- more -->

## 压缩

- 将"Demo"目录压缩成"Demo.tar.gz"压缩包，并存放在"下载"目录

``` bash
tar -zcvf ~/Downloads/Demo.tar.gz ~/Downloads/Demo/
```

## 解压

- 将"Demo.tar.gz"压缩包解压成"Demo"目录，并存放在当前文件夹

``` bash
tar -zxvf ~/Downloads/Demo.tar.gz
```

## 参考文献

[开源中国](https://wangchujiang.com/linux-command/c/tar.html)
