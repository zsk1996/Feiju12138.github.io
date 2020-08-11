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

### Servlet继承关系

![01.png](/images/20200510103051/01.png)

### 继承`HttpServlet`类

``` java
public class Servlet extends HttpServlet {
    ...	
}
```

## 请求 request


### 处理请求

#### 处理GET请求

- 默认处理GET请求
- 重写`doGet`方法

``` java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ...
}
```

#### 处理POST请求

- 重写`doPost`方法

``` java
protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    ...	
}
```

### 设置请求编码

- 针对POST提交的中文乱码
- 对于GET提交tomcat高版本已不出现乱码

``` java
req.setCharacterEncoding("utf-8");
```

### 获取请求头的信息

#### 获取URL

- 返回StringBuffer类型

``` java
req.getRequestURL();
```

#### 获取URI

``` java
req.getRequestURI();
```

#### 获取所有的请求参数

``` java
req.getQueryString();
```

#### 获取ip地址

``` java
req.getRemoteAddr();
```

#### 获取客户端主机名

``` java
req.getRemoteHost();
```

#### 获取全部请求头

``` java
Enumeration<string> reqHeaderNames = req.getHeaderNames();
while(reqHeaderNames.hasMoreElements()) {
    String headerNames = req.HeaderNames.nextElement();
    String headerValue = req.getHeader(headerNames);
    System.out.println(headerNames + ":" + headerValue);
}
```

### 获取请求参数

- 浏览器发给服务器的参数叫请求参数
- 通过请求参数名，获取请求参数值
- 请求为空时，返回null
- 如果获取多个参数的请求时使用获取单个值的方法，则只返回第一个值

> `<string>`：参数名（键）

``` java
String <string> = req.getParameter("<string>");
String[] <string> = req.getParameterValues("<string>");
```

#### 处理表单请求

``` java
req.getParameter("text");
req.getParameter("radio");
req.getParameter("select");
req.getParameter("textarea");
req.getParameter("hidden");
req.getParameterValues("checkbox");
```

### 作为域对象

- request在实现转发时，通过request.setAttribute方法和request.getAttribute方法带数据到目的地时，就是通过request对象中的map集合带数据，这个request对象上的map集合以及request对象所在的范围即称之为是一个域对象。

> `<key>`：键，必须是字符串类型
> `<value>`：值，可以是任意类型

``` java
request.setAttribute(<key>, <value>);
request.getAttribute(<key>);
```

## 响应 response

### 设置响应类型

``` java
resp.setContentType("text/html");
```

#### 设置字符集

``` java
resp.setContentType("text/html; charset=utf-8");
```

### 创建输出流对象

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

## Servlet调用过程

![02.png](/images/20200510103051/02.png)

## 请求转发（服务器端跳转）

- 余下代码后执行，先跳转
- 转发是一次请求，一次响应
- 请求转发前后，浏览器的地址栏地址不会发生变化
- 请求转发前后的request对象是同一个，可以传递参数
- 请求转发前后的两个资源必须属于同一个Web应用，否则将无法进行转发

> `<name>`：另一个资源的路径名

``` java
req.getRequestDispatcher("<name>").forward(req, resp);
```

## 目标重定向（客户端跳转）

- 余下代码先执行，后跳转
- 重定向是两次请求，两次响应
- 重定向前后，浏览器的地址栏地址会发生变化
- 重定向前后的request对象不是同一个
- 重定向前后的两个资源可以是来自不同的web应用，甚至可以是来自不同的服务器

``` java
resp.sendRedirect("<name>");
```

## 完成
