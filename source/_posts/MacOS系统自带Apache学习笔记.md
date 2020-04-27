---
title: 【笔记】MacOS系统自带Apache学习笔记
categories:
  - Server
date: 2020-02-27 00:53:32
---

## 前言

MacOS系统自带Apache学习笔记

<!-- more -->

## 基本命令

### 启动服务器

``` sh
apachectl start
apachectl -k start
```

### 重启服务器

``` sh
apachectl restart
apachectl -k restart
```

### 关闭服务器

``` sh
apachectl stop
apachectl -k stop
```

## Apache的路径

### 软件包位置

- `/private/etc/apache2`

### 配置文件位置

- `/private/etc/apache2/httpd.conf`

### 站点资源位置

- `/Library/WebServer/Documents`

## 完成

## 参考文献

[简书——弦歌芳华](https://www.jianshu.com/p/c503ef7153c2)

