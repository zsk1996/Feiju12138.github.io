---
title: 【笔记】Jsp学习笔记
categories:
  - Java
date: 2020-05-15 08:35:34
---

## 前言

在HTML中嵌入Java代码

<!-- more -->

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

## 原理

- Jsp将HTML页面代码转换为Servlet后显示，所以必须在服务器上运行

## 9大内置对象

- 在Jsp中可以直接使用的对象

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

