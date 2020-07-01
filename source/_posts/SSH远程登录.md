---
title: 【笔记】SSH远程登录
categories:
  - Linux
date: 2020-07-01 17:32:47
---

## 前言

ssh远程连接到其他主机的终端

<!-- more -->

## 远程连接

> `<host_name>`：主机名或主机IP地址

``` sh
ssh <host_name>
```

### 指定身份远程连接

> `<user_name>`：用户名

``` sh
ssh <user_name>@<host_name>
```

### x11转发

- 将远程连接的主机的包含界面的程序显示在本机

#### 允许x11转发

``` sh
ssh -X <host_name>
```

#### 禁止x11转发

``` sh
ssh -x <host_name>
```

## 完成

## 参考文献

[CSDN——IT1995](https://blog.csdn.net/qq78442761/article/details/83898442)

