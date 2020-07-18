---
title: 【笔记】String 学习笔记
categories:
  - Java
date: 2020-02-13 15:22:25
---

## 前言

Java对字符串的操作

<!-- more -->

## 查找字符串

- 返回`int`类型的值

> `<string>`：原字符串
> `<str>`：需要查找的字符串
> `<num>`：下标数

### 查找字符串的位置

``` java
<string>.indexOf(<str>);
```

### 从指定位置查找（重载方法）

``` java
<string>.indexOf(<str>, <num>);
```

### 查找最后一次出现指定字符串的位置

``` java
<string>.lastIndexOf(<str>);
```

## 截取字符串

- 返回`String`类型的值

> `<num_first>`：下标起始值
> `<num_last>`：下标截止值

### 通过指定下标截取

``` java
<string>.substring(<num_first>, <num_last>);
```

### 从指定位置开始到末尾（重载方法）

``` java
<string>.substring(<num_first>);
```

## 去除字符串两侧的空白字符

- 返回`String`类型的值

``` java
<string>.trim();
```

## 获取字符串中的字符

- 返回`char`类型的值

``` java
<string>.charAt(<num>);
```

## 判断字符串起止字符

- 返回`boolean`类型的值

### 判断字符串是否以指定字符串起始

``` java
<string>.startsWith(<str>);
```

### 判断字符串是否以指定字符串截止

``` java
<string>.endsWith(<str>);
```

## 转换字符串大小写

- 返回`String`类型的值

### 将字符串小写转换为大写

``` java
<string>.toUpperCase();
```

### 将字符串大写转换为小写

``` java
<string>.toLowerCase();
```

## 将其他类型转换为字符串

- 返回`String`类型的值

> `<other>`：其他类型的值

``` java
String.valueOf(<other>);
```

## 指定字符串拼接到当前字符串末尾

``` java
<string>.concat(<str>);
```

## 替换字符

- 替换所有出现的旧字符为新字符

> `<char_old>`：替换前的字符
> `<char_new>`：替换后的字符

``` java
<string>.replace(<char_old>, <char_new>);
```

## 转换为byte数组

- 返回char对应的byte值的数组

``` java
<string>.getBytes();
```

## 转换为char数组

- 返回char数组

``` java
<string>.toCharArray();
```

## 正则表达式的应用

> `<regular>`：正则表达式为内容的字符串

### 字符串验证

- 返回`boolean`类型的值

``` java
<string>.matches(<regular>);
```

### 字符串拆分

``` java
<string>.split(<regular>);
```

### 指定字符串替换

``` java
<string>.replaceAll(<regular>, <str>);
```

## 完成

## 参考文献

达内教育

