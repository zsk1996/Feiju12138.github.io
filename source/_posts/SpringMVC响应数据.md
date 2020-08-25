---
title: 【笔记】Spring MVC 响应数据
categories:
  - Java
date: 2020-08-24 11:40:14
---

## 前言

Spring MVC 响应数据

<!-- more -->

## 数据传输

- 通过Model传输数据

> `<key>`：键，仅可以字符串类型
> `<value>`：值，可以任意类型

``` java
@RequestMapping("/testModel")
public String testModel(Model model) {
    model.addAttribute(<key>, <value>);
    ...
    return "";
}
```

## 请求转发

### 转发到jsp

- 直接在return以字符串的形式返回jsp文件的名

> `index`：返回到index.jsp

``` java
@RequestMapping("/testForward")
public String testForward() {
    ...
    return "index";
}
```

### 转发到其他位置

- 在return加前缀`forward:`

``` java
@RequestMapping("/testForward")
public String testForward() {
    ...
    return "forward:/testParam";
}
```

## 目标重定向

### 重定向到站内

- 在SpringMVC中目标重定向也可以通过Model传递参数
- 在return加前缀`redirect:`

``` java
@RequestMapping("/testRedirect")
public String testRedirect() {
    ...
    return "redirect:/testParam";
}
```

### 重定向到站外

``` java
@RequestMapping("/testRedirect")
public String testRedirect() {
    ...
    return "redirect:/http://localhost:8080/";
}
```

## 完成

