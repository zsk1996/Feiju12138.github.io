---
title: 【笔记】Rsync 学习笔记
categories:
  - Linux
date: 2020-02-01 21:27:41
---

## 前言

`rsync`是Unix下的一款应用软件，它能同步更新两处计算机的文件与目录，并适当利用差分编码以减少数据传输量。rsync中的一项同类软件不常见的重要特性是每个目标的镜像只需发送一次。rsync可以拷贝／显示目录内容，以及拷贝文件，并可选压缩以及递归拷贝。（[维基百科](https://zh.wikipedia.org/wiki/Rsync)）

<!-- more -->

## 基本命令

### 仅指定ip地址

- 需要确认远程用户名及密码

> `-a`：归档拷贝
> `-v`：显示日志
> `<local_file>`：本地文件名
> `<remote_file>`：远程文件名或目录名
> `<ip_address>`：远程ip地址

``` sh 
rsync -av <ip_address>:<remote_file> <local_file>
```

### 指定用户名

- 需要确认远程密码

> `<user_name>`：远程用户名

``` sh
rsync -av <user_name>@<ip_address>:<remote_file> <local_file>
```

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

