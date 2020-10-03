---
title: 【踩坑】IDEA Spring Boot DI 注入报错
categories:
  - Java
date: 2020-09-23 08:07:34
---

## 前言

踩坑：IDEA Spring Boot DI 注入报错

<!-- more -->

## 原因

- `@Autowired`注解为类型注入，`@Resource`注解为名称注入
- IDEA在检查`@Autowired`拼写时，会查找Bean对象，但是有些时候我们是通过添加@ComponentScan注解，使用Spring包扫描，来自动定义Bean对象。
- 所以IDEA找不到Bean，所以会报错，但可以正常编译和运行

## 解决问题

1. 将包扫描改为在类上定义Bean

2. 将所有`@Autowired`注入改为`@Resource`注入

3. 或者暴力的通过降低IDEA警告等级来解决

- `IntelliJ IDEA`->`Preferences`->`Editor`->`Inspactions`->搜索`Spring`->选中`Autowiring for bean class`并将`Serverity`的值由`Error`改为`Warning`

![01.png](/images/20200923080734/01.png)

## 完成

## 参考文献

[CSDN——HeatDeath](https://blog.csdn.net/HeatDeath/article/details/79691506)
[segmentfault——御龙镜中潜](https://segmentfault.com/a/1190000019766877)
