---
title: 【笔记】Java运行时参数
categories:
  - Java
date: 2020-09-14 08:21:25
---

## 前言

Java运行时参数

<!-- more -->

## 项目运行时参数参数

- 在`Program arguments`添加参数
- 多个参数用空格隔开

## JVM运行时参数

- 在`VM options`添加参数
- 多个参数用空格隔开

### 跟踪类的加载过程

> `+`：添加参数
> `-`：减少参数

``` sh
-XX:+TraceClassLoading
```

### 显示GC执行过程

``` sh
-XX:+PrintGCDetails
```

## 完成
