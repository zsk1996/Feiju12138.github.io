---
title: 【笔记】Nginx负载均衡
categories:
  - Server
date: 2020-02-29 09:42:33
---

## 前言

Nginx负载均衡配置实例

<!-- more -->

## 准备工作

- 开启两个不同端口的服务

### Tomcat

- 在Tomcat服务器创建`/edu/a.html`网页文件

![01.png](/images/20200229094233/01.png)

### Apache

- 在Apache服务器创建`/edu/a.html`网页文件

![02.png](/images/20200229094233/02.png)

- 修改配置文件，将端口号改为`8081`

### 启动

- 启动`Tomcat`和`Apache`并查看端口占用情况

- 启动`Nginx`并查看端口占用情况

![03.png](/images/20200229094233/03.png)

## 编辑配置文件

``` sh
vim /usr/local/etc/nginx/nginx.conf
```

## 修改配置文件

### http 块

- 添加一个`upstream块`，自定义名称

``` sh
upstream myserver {
    server 127.0.0.1:8080 weight=1;
    server 127.0.0.1:8081 weight=1;
}
```

### server 块

``` sh
listen 80;
server_name 127.0.0.1;
```

### location 块

- 增加`proxy_pass`，值为刚创建的`upstream块名`，增加`proxy_connect_timeout`，超时时间

``` sh
location / {
    ...
    proxy_pass http://myserver;
    proxy_connect_timeout 10;
}
```

## Nginx分配服务器策略

### 轮询（默认）

- 每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除

### 权重

- weight代表权重，默认为1，权重越高被分配的客户端越多

``` sh
upstream server_pool {
    server 127.0.0.1:8080 weight=1;
    server 127.0.0.1:8081 weight=1;
}
```

### ip\_hash

- 每个请求访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决seccion问题

``` sh
upstream server_pool {
    ip_hash;
    server 127.0.0.1:8080;
    server 127.0.0.1:8081;
}
```

### fair（第三方）

- 按后端服务器的响应时间来分配请求，响应时间短的优先分配

``` sh
upstream server_pool {
    server 127.0.0.1:8080;
    server 127.0.0.1:8081;
    fair;
}
```

## 完成

- 截图纪念

![04.gif](/images/20200229094233/04.gif)

![05.gif](/images/20200229094233/05.gif)

## 参考文献

[哔哩哔哩——尚硅谷官方](https://www.bilibili.com/video/av68136734)

