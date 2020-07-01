---
title: 【笔记】Redis安装笔记
categories:
  - 云计算
date: 2020-06-17 10:53:33
---

## 前言

在`CentOS 7`安装Redis

<!-- more -->

## 准备工作

- `yum install gcc-c++`

## 查看最新版本

- [http://download.redis.io/releases/](http://download.redis.io/releases/)

## 下载并解压源码包

- `stable`是最新版

``` sh
wget http://download.redis.io/releases/redis-stable.tar.gz
tar -zxvf redis-stable.tar.gz
```

## 编译安装

``` sh
cd redis-stable
make
```

## 配置

### 编辑配置文件

``` sh
vim redis.conf
```

### 修改配置文件

- 修改为后台启动，`daemonize`改为`yes`

``` sh
daemonize yes
```

- 允许远端登录，给`bind 127.0.0.1`添加注释

``` sh
# bind 127.0.0.1
```

- `protected-mode`改为`no`

``` sh
protected-mode no
```

## 启动Redis

[传送门](/2019/12/05/redis启动关闭服务/)

## 完成

## 参考文献

[博客园——zhuzhipeng](https://www.cnblogs.com/mracale/p/11328327.html)
[简书——DevOps海洋的渔夫](https://www.jianshu.com/p/79737bc39396)
[CSDN——东风麦芽糖](https://blog.csdn.net/qq_33417321/article/details/88924934)

