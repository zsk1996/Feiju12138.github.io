---
title: 【踩坑】mysql修改简单密码报错
date: 2019-11-16 16:04:04
tags:
---

## 前言

随着mysql版本增高，安全性也逐渐变高，默认无法设置简单密码，但通常情况下安装mysql的用途是做测试，没有必要设置太难的密码，况且密码太难也记不住，通过修改mysql的安全性策略设置简单密码

<!-- more -->

## 进入mysql

- 如果是初始化创建密码阶段，先设置一个能通过mysql安全策略的难密码，然后开启mysql服务，通过命令行登录mysql

- 如果是修改密码阶段，直接启动mysql服务，登录mysql即可

- 我使用的MacOS，安装方式HomeBrew，不同系统不同安装方式的mysql开启服务的方式可能不同

``` bash
mysql.server start
mysql -u root -p
```

## 修改mysql安全性策略

- 查看当前mysql安全性策略

``` bash
mysql> SHOW VARIABLES LIKE 'validate_password%';
```

- 修改mysql安全性策略

- 我的mysql版本为8.0，请根据自己的版本修改自己的"Variable_name"值

``` bash
mysql> set global validate_password.length=4;
mysql> set global validate_password.mixed_case_count=0;
mysql> set global validate_password.number_count=0;
mysql> set global validate_password.special_char_count=0;
```

- 再次查看，确认修改成功

``` bash
mysql> SHOW VARIABLES LIKE 'validate_password%';
```

![01.png](/images/20191116160404/01.png)

## 修改密码

``` bash
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('123456');
```

## 完成

## 参考文献

[CSDN——kuluzs](https://blog.csdn.net/kuluzs/article/details/51924374)

