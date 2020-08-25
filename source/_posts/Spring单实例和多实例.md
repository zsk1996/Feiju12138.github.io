---
title: 【笔记】Spring单实例和多实例
categories:
  - Java
date: 2020-08-22 09:45:57
---

## 前言

通过`applicationContext.xml`中`bean`标签的`scope`属性控制Spring创建对象的单实例和多实例

<!--more-->

## 单例

> `id`：存储在map中的key名
> `class`：类的全局限定名
> `scope`：控制实例
>> `singleton`：单实例
>> `prototype`：多实例

``` xml
<bean id="" class="" scope=""></bean>
```

## 完成

