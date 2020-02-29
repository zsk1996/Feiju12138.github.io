---
title: 【笔记】Nginx反向代理
categories:
  - Server
date: 2020-02-28 19:15:23
---

## 前言

Nginx反向代理配置实例

<!-- more -->

## 准备工作

- 安装Nginx

- 安装Tomcat，使用默认端口8080

## 编辑配置文件

``` sh
vim /usr/local/etc/nginx/nginx.conf
```

## 修改配置文件

### 全局 server 块

- `server_name`的值改为本机ip地址

### location 块

- 增加`proxy_pass`，值为转发路径

``` sh
location / {
    root   html;
    proxy_pass  http://127.0.0.1:8080;
    index  index.html index.htm;
}
```

## 完成

## 参考文献

[哔哩哔哩——尚硅谷官方](https://www.bilibili.com/video/av68136734)

