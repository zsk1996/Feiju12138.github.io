---
title: 【笔记】JSTL学习笔记
categories:
  - Java
date: 2020-05-25 10:47:37
---

## 前言

JSP标准标签库（JSP Standard Tag Library）是Java EE网络应用程序开发平台的组成部分。它在JSP规范的基础上，扩充了一个JSP的标签库来完成一些通用任务，比如XML数据处理、条件执行、数据库访问、循环和国际化。
JSTL是在JCP下，作为JSR 52被开发出来的。（[维基百科](https://zh.wikipedia.org/wiki/JSTL)）

<!-- more -->

## 准备工作

- 在项目中导入以下jar包

`jsf-api.jar`、`jsf-impl.jar`、`jstl-1.2.jar`

## 导入JSTL标签库

- 在jsp的HTML代码之上添加代码

``` jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

## 判断语句

### if语句

> `<el>`：EL表达式，做判断

``` jsp
<c:if test="<el>">
    ...
</c:if>
```

### choose语句

- 利用`<c:otherwise></c:otherwise>`语句取反

``` jsp
<c:choose>
    <c:when test="<el>">
        ...
    </c:when>
    <c:otherwise>
        ...
    </c:otherwise>
</c:choose>
```

## 循环语句

> `<el>`：EL表达式，表示java中`for each`循环`:`后面表示的内容

``` jsp
<c:forEach items="<el>">
    ...
</c:forEach>
```

## 完成

