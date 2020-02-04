---
title: 【踩坑】JDBC 报错 Loading class `com.mysql.jdbc.Driver' ...
categories:
  - JDBC
date: 2020-01-25 22:40:23
---

## 前言

运行`JDBC`代码后，报错：``Loading class `com.mysql.jdbc.Driver'. This is deprecated. The new driver class is `com.mysql.cj.jdbc.Driver'. The driver is automatically registered via the SPI and manual loading of the driver class is generally unnecessary.``

<!-- more -->

## 原因

- `mysql 8.0`在注册驱动的时候应该是`com.mysql.cj.jdbc.Driver`，而`mysql 5.0`在注册驱动的时候才是`com.mysql.jdbc.Driver`

## 问题解决

- 将注册驱动改为`com.mysql.jdbc.Driver`

``` java
Class.forName("com.mysql.jdbc.Driver");
```

- 亦或者无需注册

## 完成

