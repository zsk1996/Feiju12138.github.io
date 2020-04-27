---
title: 【骚操作】修改 MySQL 提示符
date: 2019-12-05 17:02:57
tags:
categories:
- Database
---

## 前言

在登陆进入mysql数据库后，mysql的初始提示符只是一个很简单内容`mysql>`，没有其他任何信息。通过修改提示符，可以自定义提示信息。

<!-- more -->

## 修改提示符

- 可修改参数

> `\D`完整日期
> `\d`当前数据库
> `\h`服务器名称
> `\u`当前用户
> 自定义字符串

### 登录时直接显示修改后的提示符

``` bash
mysql -u root -p --prompt <提示符>
```

### 登入后通过命令修改提示符

``` mysql
mysql> PROMPT <提示符>
```

## 参考文献

[CSDN——Leo-Woo](https://blog.csdn.net/IMW_MG/article/details/78290149)

