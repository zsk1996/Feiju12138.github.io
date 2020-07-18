---
title: 【笔记】This 关键字
categories:
  - Java
date: 2020-07-10 11:08:57
---

## 前言

Java OOP this 关键字学习笔记

<!-- more -->

## 关键字

- this代表本类对象的引用，底层会创建本类对象

1. 当成员变量和局部变量同名时，通过this关键字来实现调用成员变量

> `<class>`：类名

``` java
class <class> {
    int a;

    public <class>() {
        this.a;
    }
}
```

2. 在构造方法中互相调用，且位置必须是第一条语句

``` java
class <class> {
    int a;

    public <class>(int a) {
        this();
    }
    
    public <class>() {
        ...
    }
}
```

## 完成

