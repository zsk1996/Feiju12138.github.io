---
title: 【笔记】更换 Kali Linux 更新源
date: 2019-11-03 18:48:39
tags:
categories:
- Linux
---

## 前言

安装完linux系统，首先要做的就是更新本地软件仓库，从远程软件仓库下载一些基本软件到本地软件仓库。然而如果不能科学上网，第一件事就要先更换更新源，至国内镜像站。

<!-- more -->

## 搜索国内镜像站地址

- 百度上可以搜到很多国内镜像站地址，在这里我从CSDN上找到了阿里云的国内镜像站地址，提供给大家

``` bash
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse

```

## 修改本地"sources.list"文件

- 使用vim编辑器，将更新源地址复制到"sources.list"文件末尾

``` bash
vim /etc/apt/sources.list
```

![01.png](/images/20191103184839/01.png)

- 保存，退出，更新源更换成功

## 参考文献

[CSDN——qq_39263240](https://blog.csdn.net/qq_39263240/article/details/79342582)
