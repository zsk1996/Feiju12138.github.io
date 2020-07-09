---
title: 【笔记】BigInteger学习笔记
categories:
  -  Java
date: 2020-07-06 10:41:55
---

## 前言

BigInteger学习笔记

<!-- more -->

## 创建对象

> `<num>`：任何类型的数字，如：`String`、`byte`、`short`、`int`、`long`

``` java
BigInteger bigInteger = new BigInteger(<num>);
```

### 创建的同时进行进位转换

> `<num>`：String类型的数字
> `<carry_old>`：原数的进位数
> `<carry_new>`：改变后的进位数

``` java
String bigInteger = new BigInteger(<num>, <carry_old>).toString(<carry_new>);
```

## 转换为其他基本类型的数字

``` java
bigInteger.byteValue()
bigInteger.shortValue()
bigInteger.intValue()
bigInteger.longValue()
bigInteger.floatValue()
bigInteger.doubleValue()
```

## 常用方法

### 返回当前大整数的绝对值

``` java
bigInteger.abs()
```

### 返回当前大整数的相反数

``` java
bigInteger.negate()
```

### 返回两个大整数的和

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.add(bigInteger_2);
```

### 返回两个大整数的差

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.subtract(bigInteger_2);
```

### 返回两个大整数的积

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.multiply(bigInteger_2);
```

### 返回两个大整数的商

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.divide(bigInteger_2);
```

### 返回当前大整数的乘方

> `<num>`：指数

``` java
bigInteger.power(<num>);
```

### 返回当前大整数的模

> `<num>`：除数

``` java
bigInteger.remainder(<num>)
```

### 返回大整数的最大公约数

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.gcd(bigInteger_2);
```

### 返回两个大整数的最大者

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.max(bigInteger_2);
```

### 返回两个大整数的最小者

``` java
BigInteger bigInteger_1 = new BigInteger(<num>);
BigInteger bigInteger_2 = new BigInteger(<num>);
bigInteger_1.min(bigInteger_2);
```

### 将当前大整数转换成十进制的字符串形式

``` java
bigInteger.toString();
```

## 参考文献

[博客园——小小范同学](https://www.cnblogs.com/numen-fan/p/6500914.html)
[CSDN——大前端码农的自我修养](https://blog.csdn.net/jiangguangchao/article/details/101520017)

