---
title: 【笔记】Junit单元测试
categories:
  - Java
date: 2020-07-27 20:57:58
---

## 前言

Java Junit 单元测试 学习笔记

<!-- more -->

## 单元测试

1. 定义一个测试类，类名通常为`被测试类名Test`，包名通常为`被测试包名.test`

2. 定义测试方法，方法名通常为`test被测试方法名()`，返回值为`void`，参数列表为空

3. 添加注解`@Junit`

4. 倒入Junit依赖

## 断言

- 断言一个结果，与测试的结果做对比，从而判断程序是否有错误，而不是直接输出结果到控制台

> `<think>`：断言的结果
> `<result>`：程序返回的结果

``` java
Assert.assertEuqals(<think>, <result>);
```

- 当断言失败时，控制台会打印异常

### 初始化方法

- 在所有测试方法执行之前执行该方法

``` java
@Before
public void init() {
    ...
}
```

### 资源释放方法

- 在所有测试方法执行之后执行该方法

``` java
@After
publuc void close() {
    ...
}
```

## 完成

## 参考文献

[哔哩哔哩——黎曼的猜想](https://www.bilibili.com/video/BV1uJ411k7wy?p=460)

