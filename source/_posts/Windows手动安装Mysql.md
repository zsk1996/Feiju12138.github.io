---
title: 【笔记】Windows手动安装Mysql
categories:
  - Windows
date: 2020-09-13 17:32:54
---

## 前言

Windows手动安装Mysql 5.7.30

<!-- more -->

## 准备工作

- Mysql 5.7.30 Windows ZIP Archive [传送门](https://downloads.mysql.com/archives/community/)

## 开始安装

- 初始化

``` sh
mysqld --initialize --user=mysql --console
```

- 安装服务

``` sh
mysqld -install
```

- 启动服务

``` sh
net start mysql
```

### 踩坑

- 报错：`Install/Remove of the Service Denied!`

- 原因：权限不足

- 解决问题：用管理员身份打开cmd

### 踩坑

- 默认有初始密码且找不到

#### 解决问题

- 关闭mysql服务

``` sh
net stop MySQL
```

- 先用一个cmd通过安全模式启动mysql服务

``` sh
mysqld --skip-grant-tables
```

- 再打开另一个新的cmd无密码进入mysql，再修改密码

``` sh
mysql -u root -p
```

### 踩坑

- 在安全模式修改密码报错：`The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement`

#### 解决问题

- 先执行

``` sh
flush privileges;
```

- 再改密码

``` sh
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
```

## 完成

## 参考文献

[CSDN——geekcloud](https://blog.csdn.net/geeksoarsky/article/details/84113009)
[博客园——小德cyj](https://www.cnblogs.com/dongzhuangdian/p/5620771.html)
[博客园——无泪人](https://www.cnblogs.com/zenghongfei/p/13304279.html)
