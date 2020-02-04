---
title: 【笔记】Scp 学习笔记
categories:
  - Linux
date: 2020-02-01 16:44:29
---

## 前言

安全复制是指在本地主机与远程主机或者两台远程主机之间基于Secure Shell协议安全地传输计算机文件。“SCP”通常指安全复制协议或者程序本身。（[维基百科](https://zh.wikipedia.org/zh-cn/安全复制)）

<!-- more -->

## 基本命令

> `<ip_address>`：远程ip地址
> `<user_name>`：远程用户名
> `<local_file>`：本地文件名
> `<remote_file>`：远程文件名或目录名

### 本地文件发送远程

#### 仅指定ip地址

- 需要确认远程用户名及密码

``` sh
scp <local_file> <ip_address>:<remote_file>
```

#### 指定用户名

- 需要确认远程密码

``` sh
scp <local_file> <user_name>@<ip_address>:<remote_file>
```

#### 指定端口号

``` sh
scp -P 22 <local_file> <ip_address>:<remote_file>
scp -P 22 <local_file> <user_name>@<ip_address>:<remote_file>
```

### 远程文件发送远程

> `<ip_address_1>`：远程1的ip地址
> `<file_1>`：远程1的文件 
> `<ip_address_2>`：远程2的ip地址
> `<file_2>`：远程2的文件或目录

``` sh
scp <ip_address_1>:<file_1> <ip_address_2>:<file_2>
```

## 参考文献

[菜鸟笔记](https://www.runoob.com/linux/linux-comm-scp.html)

