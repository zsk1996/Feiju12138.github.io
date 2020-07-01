---
title: 【笔记】Mysql数据库名不允许有横线
categories:
  - Database
date: 2020-06-17 10:42:24
---

## 前言

Mysql数据库名有横线报错：`You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-vue' at line 1`

<!-- more -->

## 解决问题

- 在创建数据库时将数据库名用\``括起来

``` mysql
CREATE DATABASE `ry-vue`
```

## 完成

## 参考文献

[CSDN——码之魂](https://bbs.csdn.net/topics/390609696)

