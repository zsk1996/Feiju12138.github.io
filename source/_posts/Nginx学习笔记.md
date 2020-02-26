---
title: 【笔记】Nginx 学习笔记
categories:
  - 服务器
date: 2020-02-22 00:30:32
---

## 前言

Nginx学习笔记

<!-- more -->

## 安装Nginx

### Nginx版本

1. 开发版

Mainline version

2. 稳定版

Stable version

3. 历史版本

Legacy version

### MacOS

``` sh
brew install nginx
```

### CentOS 7

- 新建`.repo`文件

``` sh
vim /etc/yum.repos.d/nginx.repo
```

- 编辑`.repo`文件

> `<OS>`：系统，如`centos`
> `<OSRELEASE>`：系统版本，如`7`

``` sh
[nginx]
name=nginx repo
baseurl=http://nginx.org/package/<OS>/<OSRELEASE>/$basearch/
gpgcheck=0
enabled=1
```

## 目录结构

|路径|类型|作用|
|---|---|---|
|/etc/nginx<br>/etc/nginx/nginx.conf<br>/etc/nginx/conf.d<br>/etc/nginx/conf.d/default.conf|配置文件|Nginx主配置文件|
|/etc/nginx/fastcgi\_params<br>/etc/nginx/scgi\_params<br>/etc/nginx/|配置文件|Cgi、Fastcgi、Uwcgi配置文件|
|/etc/nginx/win-utf<br>/etc/nginx/koi-utf<br>/etc/nginx/koi-win|配置文件|Nginx编码转换映射文件|
|/etc/nginx/mime.types|配置文件|http协议的Content-Type|
|/etc/rc.d/init.d/nginx<br>/etc/rc.d/init.d/nginx-debug<br>/etc/sysconfig/nginx<br>/etc/sysconfig/nginx-debug|配置文件|配置系统守护进程管理器|
|/etc/logrotate.d/nginx|配置文件|Nginx日志轮询，日志切割|
|/usr/sbin/nginx<br>/usr/sbin/nginx-debug|命令|Nginx终端管理命令|
|/usr/share/doc/nginx-1.12.2<br>/usr/share/man/man8/nginx.8.gz|目录|Nginx的帮助手册|
|/var/cache/nginx|目录|Nginx的缓存目录|
|/var/log/nginx|目录|Nginx的日志目录|
|/etc/nginx/modules<br>/usr/lib64/nginx<br>/usr/lib64/nginx/modules|目录|Nginx模块目录|
|/usr/share/nginx<br>/usr/share/nginx/html<br>/usr/share/nginx/html/50x.html<br>/usr/share/nginx/html/index.html|目录|Nginx默认站点目录|

## 基本命令

### 启动Nginx

``` sh
nginx
```

#### 指定配置启动

- 默认使用`/etc/nginx/nginx.conf`配置文件启动nginx

``` sh
nginx -c /etc/nginx/nginx.conf
```

##### 验证配置文件

``` sh
nginx -t
nginx -t -c /etc/nginx/nginx.conf
```

### 重新加载

- 可以重启其它文件启动的情况

``` sh
nginx -s reload
```

### 快速停止

``` sh
nginx -s stop
```

### 正常停止

``` sh
nginx -s quit
```

### 查看版本

``` sh
nginx -v
```

## 服务器状态码

### 常见

|状态码|含义|备注|
|---|---|---|
|301|永久移动|请求的资源已经被永久移动位置|
|302|临时移动|请求的资源现在临时从不同的URI响应请求|
|305|使用代理|被请求的资源必须通过指定的代理才能被访问|
|307|临时跳转|请求的资源在临时从不同的URL响应请求|
|400|错误请求|
|402|需要付款|该状态码是为了将来可能的需求而预留的，用于一些数字货币或者是微支付|
|403|禁止访问|服务器已经理解请求，但是拒绝执行它|
|404|找不到对象|请求失败，资源不存在|
|406|不可接受|请求的资源的内容特性无法满足请求头中的条件，因而无法生成响应实体|

### 不常见

|状态码|含义|备注|
|---|---|---|
|408|请求超时|
|409|冲突|由于和被请求的资源的当前状态之间存在冲突，请求无法完成|
|410|遗失|被请求的资源在服务器上已经不再可用，而且没有任何已知的转发地址|
|413|相应实体太大|服务器拒绝处理当前请求，请求超过服务器所能处理和允许的最大值|
|417|期望失败|在请求头Expect中指定的预期内容无法被服务器满足|
|418|我是一个茶壶|超文本咖啡罐控制协议，但是并没有被实际的HTTP服务器实现|
|420|方法失效|
|422|不可处理的实体|请求格式正确，但是由于含有语义错误，无法响应|
|500|服务器内部错误|服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理|
|502|请求后端失败|
|504|响应超时|请求成功，但是响应超时|





## 未完待更

## 参考文献

[哔哩哔哩——做个黑客小杨](https://www.bilibili.com/video/av55251610)
[CSDN——weixin\_34356138](https://blog.csdn.net/weixin_34356138/article/details/85996493)

