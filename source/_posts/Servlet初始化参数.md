---
title: 【笔记】Servlet初始化参数
categories:
  - Java
date: 2020-05-13 11:14:46
---

## 前言

`ServletConfig对象`和`ServletContext对象`学习笔记

<!-- more -->

## 添加配置

- 在web.xml文件中，以键值对的形式添加配置参数，可以添加多组

> `<<name>>`：参数名（键）
> `<<value>`：参数值（值）

``` xml
<init-param>
    <param-name><<name>></param-name>
    <param-value><<value>></param-value>
</init-param>
```

## 获取Servlet初始化参数对象

``` java
ServletConfig config = this.getServletConfig();
```

## 读取参数

### 通过键读取值

``` java
config.getInitParameter("<<name>>");
```

### 读取所有的键

``` java
Enumeration<String> names = config.InitParameterNames();
while(names.hasMoreElements()) {
    String name = names.nextElement();
}
```

## 设置字符集

- 解决中文乱码

``` java
req.setCharacterEncoding("utf-8");
```

## 获取ServletContext对象

- 项目上下文对象，代表整个项目
- 三种方法

``` java
ServletContext context = this.getServletContext();
ServletContext context = req.getServletContext();
ServletContext context = this.getServletConfig().getServletContext();
```

## 获取资源名

``` java
getServletName()
```

## 获取资源位置

``` java
context.getReadPath(getServletName());
```

## 写入Context数据

- 保存需要长久保存的数据（只要不关闭服务器就可以一直保存）

> `<key>`：数据名（键）
> `<value>`：数据值（值）

``` java
context.setAttribute("<key>", "<value>");
``` 

## 读取Context数据

``` java
context.getAttribute("<key>", "<value>");
```

## 参考文献

达内教育

