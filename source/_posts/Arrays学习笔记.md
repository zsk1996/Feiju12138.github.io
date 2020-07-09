---
title: 【笔记】Arrays学习笔记
categories:
  - Java
date: 2020-07-07 16:20:19
---

## 前言

Arrays工具类学习笔记

<!-- more -->

## 复制数组

> `<array_old>`：原数组
> `<length>`：新数组长度（等于原数组长度）

``` java
Arrays.copyOf(<array_old>, <length>);
```

### 数组扩容

> `<length+>`：新数组长度（大于原数组的长度）

``` java
Arrays.copyOf(<array_old>, <length+>);
```

### 数组缩容

> `<length->`：新数组长度（小于原数组的长度）

``` java
Arrays.copyOf(<array_old>, <length->);
```

## 数组转化为字符串

> `<array>`：数组

``` java
Arrays.toString(<array>);
```

## 数组排序

- 默认从小到大排序
- 排序后会将原数组修改成排序后的数组（而不是产生新的排序后数组，所以直接调用原数组即可）

``` java
Arrays.sort(<array>);
```

## 完成

