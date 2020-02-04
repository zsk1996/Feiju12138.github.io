---
title: 【踩坑】JDBC 报错 The server time zone value '' ...
categories:
  - JDBC
date: 2020-01-25 23:01:52
---

## 前言

运行`JDBC`代码后，报错：``Exception in thread "main" java.sql.SQLException: The server time zone value '' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the 'serverTimezone' configuration property) to use a more specifc time zone value if you want to utilize time zone support.``

<!-- more -->

## 原因

- 没有正确设置时区

## 问题解决

- 在`jdbc:`的`?`后增加配置`serverTimezone=UTC`，多个配置用`&`隔开

值`UTC`为全球标准时间

``` java
jdbc:mysql://localhost:3306/xscj?serverTimezone=UTC
```

## 完成

## 参考文献

[CSDN——喵主子](https://blog.csdn.net/qq631431929/article/details/51731834)

