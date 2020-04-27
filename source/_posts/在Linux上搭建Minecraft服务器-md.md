---
title: 【笔记】在Linux上搭建Minecraft服务器.md
categories:
  - Minecraft
date: 2020-04-26 21:13:28
---

## 前言

在`阿里云 CentOS 7`上搭建Minecraft服务器

<!-- more -->

## 准备工作

- 对应版本的`minecraft-server`

## 安装JDK

- [传送门](/2020/04/26/Java安装笔记/)

## 初始化minecraft-server

- [传送门](/2020/03/03/在Mac上搭建Minecraft服务器/)

## 调试

- 遇到报错时，可以选择以下方法调试

### 端口转发（可选）

- 当80端口已开放时，可以进行端口转发

``` sh
iptables -I PREROUTING -t nat -p tcp --dport 80 -j REDIRECT --to-ports 25565
```

### 开放端口（可选）

- 当防火墙开启时，需要开放25565端口

``` sh
firewall-cmd --query-port=25565/tcp 
```

### 关闭防火墙（可选）

- 当防火墙开启时，可以关闭防火墙

``` sh
systemctl stop firewalld.service
```

## 完成

## 参考文献

[CSDN——病毒宇宇](https://blog.csdn.net/ziele_008/article/details/52062237)

