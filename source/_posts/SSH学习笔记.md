---
title: 【进阶】SSH 学习笔记
categories:
  - Linux
date: 2020-02-02 17:52:05
---

## 前言

Secure Shell是一种加密的网络传输协议，可在不安全的网络中为网络服务提供安全的传输环境。SSH通过在网络中创建安全隧道来实现SSH客户端与服务器之间的连接。虽然任何网络服务都可以通过SSH实现安全传输，SSH最常见的用途是远程登录系统，人们通常利用SSH来传输命令行界面和远程执行命令。([维基百科](https://zh.wikipedia.org/zh-cn/Secure_Shell)）

`Linux`开启`ssh`免密登录

<!-- more -->

## 原理

- 提前准备一对`私钥`和`公钥`，把`公钥`发给其他主机

> 私钥：`~/.ssh/id_rsa`
> 公钥：`~/.ssh/id_rsa.pub`

## 生成密钥对

- 在本机生成密钥对

> `rsa`：其中一种加密类型

``` sh
ssh-keygen -t rsa
```

### 确认私钥存放路径

- 直接`return`键设置默认值

### 输入密码

- 如果要配置免密登录，直接`return`键设置默认值

### 确认密码

- 确认刚刚设置的密码，没有密码直接`return`键设置默认值

## 发送公钥

- 把公钥发送到其他主机

> `<ip_address>`：其他主机的ip地址或主机名称

``` sh
ssh-copy-id <ip_address>
```

## 其他文件

- 其他主机的发过来的公钥在`~/.ssh/authorized_keys`文件内

- 允许其他主机登录本机的列表在`~/.ssh/known_hosts`文件内

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

