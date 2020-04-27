---
title: 【笔记】Nginx动静分离
categories:
  - Server
date: 2020-02-29 11:41:54
---

## 前言

Nginx动静分离简单来说就是把动态请求和静态请求分开，不能理解成只单纯的把动态页面和静态页面物理分离。严格意义上说应该是动态请求和静态请求分开，可以理解成使用Nginx处理静态页面，Tomcat处理动态页面。

<!-- more-->

## 静态资源部署

### 准备工作

#### 准备资源

- 创建静态资源目录

``` sh
cd /usr/local/var/www
mkdir data
mkdir data/img
mkdir data/www
```

- 在img复制一张图片做测试，命名为`01.jpg`

- 在www复制一张网页做测试，命名为`a.html`

### 编辑配置文件

``` sh
vim /usr/local/etc/nginx/nginx.conf
```

### 修改配置文件

#### location 块

``` sh
location /www/ {
    root html/data/;
    index index.html index.htm;
}
location /img/ {
    root html/data/;
    autoindex on;
}
```

### 测试截图

![01.png](/images/20200229114154/01.png)

![02.png](/images/20200229114154/02.png)

## 参考文献

[哔哩哔哩——尚硅谷官方](https://www.bilibili.com/video/av68136734)

