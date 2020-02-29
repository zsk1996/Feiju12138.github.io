---
title: 【进阶】Nginx反向代理
categories:
  - Server
date: 2020-02-28 20:19:04
---

## 前言

Nginx反向代理配置实例2

通过不同路径访问不同端口

<!-- more -->

## 准备工作

- 开启两个不同端口的服务

### Tomcat

- 在Tomcat服务器创建`/vod/a.html`网页文件

![01.png](/images/20200228201904/01.png)

### Apache

- 在Apache服务器创建`/edu/a.html`网页文件

![02.png](/images/20200228201904/02.png)

- 修改配置文件，将端口号改为`8081`

### 启动

- 启动`Tomcat`和`Apache`并查看端口占用情况

- 启动`Nginx`并查看端口占用情况

![03.png](/images/20200228201904/03.png)

## 编辑配置文件

``` sh
vim /usr/local/etc/nginx/nginx.conf
```

## 修改配置文件

### 添加一个server块

- 在server块后再添加一个server块

``` sh
server {
    listen       9001;
    server_name  127.0.0.1;

    location ~ /edu/ {
        proxy_pass  http://localhost:8080;
    }
    location ~ /vod/ {
        proxy_pass  http://localhost:8081;
    }
}
``` 

## 完成

- 截图纪念

![04.gif](/images/20200228201904/04.gif)

![05.gif](/images/20200228201904/05.gif)

## 参考文献

[哔哩哔哩——尚硅谷官方](https://www.bilibili.com/video/av68136734)

