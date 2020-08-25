---
title: 【笔记】Spring MVC 参数绑定
categories:
  - Java
date: 2020-08-24 11:20:46
---

## 前言

SpringMVC参数绑定

<!-- more -->

## 基本类型参数绑定

- 参数名必须相同，顺序可以不同
- 如果传过来参数的值包含多个，既可以由String接收（会得到用逗号分隔的拼接而成的字符串），也可以由String[]接收（会得到字符串数组）

``` java
@RequestMapping("/testParam")
public String testParam(String name, Integer age) {
    ...
    return "";
}
```

## 包装类型参数绑定

- 首先定义一个包含传过来参数名相同的属性的POJO类，并定义相关get、set、toString方法

``` java
@RequestMapping("/testParam")
public String testParam(User user) {
    ...
    return "";
}
```

## 日期类型参数绑定

- 默认SpringMVC日期类型参数需要使用`/`做间隔

``` java
@RequestMapping("/testParam")
public String testParam(Date date) {
    System.out.println(date.toLocaleString());
    ...
    return "";
}
```

### 修改默认格式化方式

- 默认SpringMVC日期类型格式化的数据需要由`/`做间隔

- 添加SpringMVC自定义日期格式转换器，将SpringMVC默认以`/`分隔改为以`-`分隔

``` java
@InitBinder
public void InitBinder (ServletRequestDataBinder binder){
    binder.registerCustomEditor(java.util.Date.class, 
        new CustomDateEditor(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss"), true)
    );
}
```

## 完成

