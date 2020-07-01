---
title: 【笔记】更换 CentOS Linux 更新源
categories:
  - Linux
date: 2020-01-31 00:53:29
---

## 前言

更换`CentOS Linux`更新源，系统版本`7`

<!-- more -->

## 换源

- 备份系统自带yum源配置文件

``` sh
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

- 下载`网易`的yum源配置文件

``` sh
cd /etc/yum.repos.d/
wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
```

- 生成缓存

``` sh
yum clean all
yum makecache
```

- 更新

``` sh
yum -y update
```

## 完成

## 参考文献

[CSDN——inslow](https://blog.csdn.net/inslow/article/details/54177191)

