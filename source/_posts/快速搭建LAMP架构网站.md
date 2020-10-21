---
title: 【笔记】快速搭建LAMP架构网站
categories:
  - Cloud Computing
date: 2020-02-23 18:02:56
---

## 前言

本文以`Discuz`论坛网站为例，实现LAMP架构（`Linux`、`Apache`、`Mysql`、`Php`）网站快速搭建

<!-- more -->

## 准备工作

- CentOS服务器（或虚拟机）

## 配置环境

- ssh连接服务器

- 安装搭建`Discuz`需要用到的软件包

``` sh
yum install httpd mariadb-server php php-mysql unzip
```

- 修改`html目录`权限

``` sh
chown -R apache /var/www/
```

## 将开发完成的项目拷贝到服务器

- 在本地使用`scp命令`实现文件传输

> `<remote_ip>`：服务器ip地址

``` sh
scp ~/Downloads/Discuz_X3.4_SC_UTF8.zip root@<remote_ip>:/root
```

- 解压项目

``` sh
unzip /root/Discuz_X3.4_SC_UTF8.zip
```

- 把项目的`upload目录下的所有文件`复制到`/var/www/html/`目录下

``` sh
cp -rf upload/* /var/www/html/
```

## 启动服务

- 启动数据库

``` sh
systemctl start mariadb
```

- 启动Apache服务器

``` sh
systemctl start httpd
```

## 完成

- 使用服务器ip地址作为域名访问服务器的网站

- 截图纪念

![01.png](/images/20200223180256/01.png)

## 参考文献

达内教育

