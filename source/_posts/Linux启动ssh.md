---
title: 【笔记】Linux 启动 ssh
categories:
  - Linux
date: 2020-01-31 16:36:04
---

## 前言

在`Linux`启动`ssh`服务

<!-- more -->

## 安装 openssh

``` sh
yum install openssh-server
```

## 修改配置

### 编辑配置文件

``` sh
vim /etc/ssh/sshd_config
```

### 去除端口号注释

``` sh
Port 22
```

### 去除监听地址注释

``` sh
ListenAddress 0.0.0.0
ListenAddress ::
```

### 允许远程登录

``` sh
PermitRootLogin yes
```

### 允许使用密码验证身份

``` sh
PasswordAuthentication yes
```

## 启动 sshd 服务

``` sh
sudo service sshd start
```

## 完成

## 参考文献

[CSDN——dh2580](https://blog.csdn.net/trackle400/article/details/52755571)

