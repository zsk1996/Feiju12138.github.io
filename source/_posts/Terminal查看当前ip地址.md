---
title: 【笔记】Terminal 查看当前ip地址
categories:
  - MacOS
date: 2020-07-14 17:17:22
---

## 前言

Terminal 查看当前公网ip地址

<!-- more -->

## 查看ip地址

``` sh
curl http://checkip.amazonaws.com/
```

### 指定代理

> `<ip>`：代理地址
> `<port>`：代理端口

``` sh
curl --socks5 <ip>:<port> http://checkip.amazonaws.com/
```

## 完成

## 参考文献

[QAStack——](https://qastack.cn/ubuntu/499995/how-to-change-the-ip-address-which-is-given-by-tor-using-the-terminal)

