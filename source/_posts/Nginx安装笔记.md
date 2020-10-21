---
title: 【笔记】Nginx安装笔记
categories:
  - Cloud Computing
date: 2020-06-17 12:00:05
---

## 前言

在`CentOS 7`上安装Nginx

<!-- more -->

## 准备工作

- `yum install gcc-c++`

- `yum install -y pcre pcre-devel`

- `yum install -y zlib zlib-devel`

- `yum install -y openssl openssl-devel`

## 查看最新版本

- [https://nginx.org/download/](https://nginx.org/download/)

## 下载软件包

``` sh
wget https://nginx.org/download/nginx-1.9.9.tar.gz
tar -zxvf nginx-1.9.9.tar.gz
```

## 编译安装

``` sh
./configure
make install
```

## 未完待更

## 参考文献

[掘金——张攀钦](https://juejin.im/post/5cffb3f76fb9a07eca69731a)

