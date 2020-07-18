---
title: 【笔记】Terminal 配置网络代理
categories:
  - MacOS
date: 2020-07-14 16:59:16
---

## 前言

在终端配置网络代理。
临时性的，关闭终端后失效。
如果想要永久性的，可以将配置信息添加到终端配置文件。

<!-- more -->

## HTTP代理

- 配置HTTP及HTTPS代理

> `<ip>`：代理地址
> `<port>`：代理端口号

``` sh
export http_proxy=http://<ip>:<port>;
export https_proxy=http://<ip>:<port>;
```

## SOCKS代理

- 配置SOCKS5代理

``` sh
export http_proxy=socks5://<ip>:<port>;
```

## 需要登录的代理

> `<username>`：用户名
> `<password>`：密码

``` sh
http_proxy=http://<username>:<password>@<ip>:<port>
```

## 完成

## 参考文献

[fazero的博客](https://blog.fazero.me/2015/09/15/让终端走代理的几种方法/)

