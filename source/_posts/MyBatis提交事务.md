---
title: 【笔记】MyBatis提交事务
categories:
  - Java
date: 2020-08-20 11:47:03
---

## 前言

使用MyBatis框架的项目，MyBatis自动开启了事务，有两种提交事务的方式，一种是自动提交，一种是每一次手动提交

<!-- more -->

## 自动提交

- 在通过工厂获取一个SqlSession对象时给定参数，达到自动提交的事务
- 适用每次只执行一条语句

``` java
session = sqlSessionFactory.openSession(true);
```

## 手动提交

- 在每次代码末尾，通过`commit()`方法手动提交事务
- 适用每次执行多条语句

``` java
session.commit();
```

## 完成

