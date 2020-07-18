---
title: 【笔记】StringBuilder 学习笔记
categories:
  - Java
date: 2020-02-13 15:40:44
---

## 前言

StringBuilder/StringBuffer 学习笔记
StringBuiler提供了用于修改字符串内容的相关方法。
其内部维护的是一个可变的字符数组，所以修改都是在当前对象内部完成的。
当频繁修改字符串内容时应当使用`StringBuilder`类来完成

<!-- more -->

## 创建 StringBuilder 对象

- 默认容量为16个字符
- 下一次扩容，为上一次容量数乘2再加2

> `<builder>`：StringBuilder类型的值

### 空字符串

``` java
StringBuilder <builder> = new StringBuilder();
```

### 非空字符串

> `<string>`：String类型的值

``` java
StringBuilder <builder> = new StringBuilder(<string>);
```

## 追加字符串到末尾

``` java
<builder>.append(<string>);
```

## 替换指定字符串为指定内容

> `<num_first>`：起始下标
> `<num_last>`：截止下标

``` java
<builder>.replace(<num_first>, <last_first>, <string>);
```

## 删除指定的字符串

``` java
<builder>.delete(<num_first>, <num_last>);
```

## 插入字符串到指定位置

> `<num>`：下标位置

``` java
<builder>.insert(<num>, <string>);
```

## 反转字符串

``` java
<builder>.reverse();
```

## 完成

## 参考文献

达内教育

