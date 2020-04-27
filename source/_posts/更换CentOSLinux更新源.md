---
title: 【笔记】更换 CentOS Linux 更新源
categories:
  - Linux
date: 2020-01-31 00:53:29
---

## 前言

更换`CentOS Linux`更新源，系统版本`8`

<!-- more -->

## 换源

- 备份系统自带yum源配置文件

``` sh
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

- 下载`ailiyun`的yum源配置文件

``` sh
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-8.repo
```

- 生成缓存

``` sh
yum makecache
```

- 更新

``` sh
yum -y update
```

## 完成

## 参考文献

[CSDN——inslow](https://blog.csdn.net/inslow/article/details/54177191)

