---
title: 【踩坑】DataGrip报错：Server returns invalid
categories:
  - Database
date: 2020-05-19 09:00:04
---

## 前言

DataGrip报错：`Server returns invalid timezone. Need to set'servertimezone property`

<!-- more -->

![01.png](/images/20200519090004/01.png)

## 原因

- 服务器返回无效时区

## 解决问题

- 将时区设置为`+8:00`

``` mysql
show variables like '%time_zone%';
set global time_zone='+8:00';
```

## 完成

## 参考文献

[CSDN——菜鸟的自我素养](https://blog.csdn.net/weixin_42941486/article/details/100660560)

