---
title: 【笔记】Jsp学习笔记
categories:
  - Java
date: 2020-05-15 08:35:34
---

## 前言

在HTML中嵌入Java代码

<!-- more -->

## 原理

- Jsp将HTML页面代码转换为Servlet后显示，所以必须在服务器上运行

## Java代码块

``` jsp
<%
    ...
%>
```

## 注释

``` jsp
<%--  --%>
```

## 指令

- 用于声明JSP的基本属性信息

### 指定当前JSP使用的开发语言

- 默认为`java`

``` jsp
<%@ page language="java"%>
```

### 导包

``` jsp
<%@ page import=""%>
```

### 指定当前JSP使用的编码

- 这个编码指定后，即使不指定`content="text/html;charset=UTF-8"`或`<meta charset="UTF-8">`中文也不会显示为乱码

``` jsp
<%@ page pageEncoding="UTF-8"%>
```

### 是否禁用EL

- `true`为禁用，`false`为启用

``` jsp
<%@ page isELIgnored=""%>
```

### 引入标签库

#### 引入JSTL标签库

- [传送门](/2020/05/25/JSTL学习笔记/)

``` jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

## 9大内置对象

- 在Jsp中可以直接使用的对象
- `page`、`resquest`、`response`、`config`、`application`、`exception`、`pageContext`、`out`、`session`

### 在页面输出

- 对应Servlet中的`PrintWrite`对象

> `<string>`：输出的内容

``` jsp
out.println("<string>");
```

#### 简化

``` jsp
<%= <string> %>
```

### 请求对象

- 对应Servlet中的`HttpServletRequest`对象

> `<method>`：方法

``` jsp
request.<method>
```

### 响应对象

- 对应Servlet中的`HttpServletResponse`

``` jsp
response.<method>
```

### 会话对象

- 对应Servlet中的`HttpSession`对象

``` jsp
session.<method>
```

### 项目上下文对象

- 对应Servlet中的`ServletContext`对象

``` jsp
application.<method>
```

### 初始化参数对象

- 对应Servlet中的`ServletConfig`对象

``` jsp
config.<method>
```

### 当前页面自身

- 相当于类中的`this`关键字

``` jsp
page
```

### 页面上下文对象

``` jsp
pageContext
```

### 异常对象

- 对应Servlet中的`Throwable`对象

``` jsp
exception.<method>
```

## Jsp中可以传递数据的对象

### pageContext（页面上下文域）

- 传值范围是当前页面

### request（请求域）

- 传值范围是同一个请求中，适用于请求转发

### session（会话域）

- 传值范围是在同一个回话内
- 只要浏览器不关闭

### application

- 传值范围是在一个项目内
- 只要服务器不关闭

## Jsp请求转发

> `<<page>>`：转发的页面

``` jsp
<jsp:forward page="<<page>>"></jsp:forward>
```

## 参考文献

达内教育

