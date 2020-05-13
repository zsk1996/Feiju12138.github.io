---
title: 【笔记】Servlet学习笔记
categories:
  - Java
date: 2020-05-10 10:30:51
---

## 前言

Servlet学习笔记

<!-- more -->

## 编写Servlet类

- 继承`HttpServlet`类

``` java
public class Servlet extends HttpServlet {
    ...	
}
```

## 处理请求

### 处理GET请求

- 默认处理GET请求
- 重写`doGet`方法

``` java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ...
}
```

### 处理POST请求

- 重写`doPost`方法

```
protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ...	
}
```

## 设置响应类型

``` java
resp.setContentType("text/html");
```

### 设置字符集

``` java
resp.setContentType("text/html; charset=utf-8");
```

## 创建输出流对象

``` java
PrintWriter out = resp.getWriter();
```

- 输出到网页

``` java
out.println("<html>");
out.println("<head>");
out.println("<title></title>");
out.println("</head>");
out.println("<body>");
out.println("</body>");
out.println("</html>");
```

## req的常用方法

### 设置请求编码

``` java
req.setCharacterEncoding("utf-8");
```

### 获取请求参数

- 请求参数为键值对，获取请求参数就是通过键获取值的过程

> `<string>`：参数名（键）

``` java
req.getParameter("<string>");
```

### 获取URL

- 返回StringBuffer类型

``` java
req.getRequestURL();
```

### 获取URI

``` java
req.getRequestURI();
```

### 获取所有的请求参数

``` java
req.getQueryString();
```

### 获取ip地址

``` java
req.getRemoteAddr();
```

### 获取客户端主机名

``` java
req.getRemoteHost();
```

### 获取客户端请求头

``` java
Enumeration<string> reqHeaderNames = req.getHeaderNames();
while(reqHeaderNames.hasMoreElements()) {
    String headerNames = req.HeaderNames.nextElement();
    String headerValue = req.getHeader(headerNames);
    System.out.println(headerNames + ":" + headerValue);
}
```

### 处理表单请求

#### 获取文本框
#### 获取单选框
#### 获取下拉列表
#### 获取文本域
#### 获取隐藏域

``` java
req.getParameter("text");
req.getParameter("radio");
req.getParameter("select");
req.getParameter("textarea");
req.getParameter("hidden");
```

#### 获取复选框

- 返回String[]类型

``` java
req.getParameterValues("checkbox");
```

## Servlet生命周期

- 当一个Servlet资源第一次被访问的时候，由服务器创建Servlet资源对象，通过调用Servlet的init()方法，完成对象的初始操作，该方法只会调用一次

- 对象完成初始化以后，服务器会调用Servlet()方法，完成相关的业务处理（执行各种操作，例如doGet或者doPost），该方法可以反复执行，每一次访问该Servlet资源都会执行该方法

- 当服务器停止的时候，服务器会调用Servlet资源的destroy()方法，用来销毁Servlet对象

### 自动初始化

- 服务器启动的时候立即创建Servlet资源对象，同时访问init()方法完成对象的初始化，其中配置是一个整数数字，最小值是1，值越小，访问的优先级越高

- 修改`web.xml`的`<servlet></servlet>`块

``` xml
<load-on-startup>1</load-on-startup>
```

## 请求转发（服务器端跳转）

- 余下代码后执行，先跳转

> `<name>`：另一个资源的路径名

``` java
req.getRequestDispatcher("<name>").forward(req, resp);
```

## 目标重定向（客户端跳转）

- 余下代码先执行，后跳转

``` java
resp.sendRedirect("<name>");
```

## 未完待更

## 参考文献

达内教育

