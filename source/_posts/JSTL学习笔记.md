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

- 在项目中导入`jstl-1.2.jar`jar包

## 导入JSTL标签库

- 在jsp的HTML代码之上添加代码

``` jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

## 域中数据的操作

- 用于往域中添加数据或修改已有数据
- 默认存入pageContext域中

> `<key>`：域中数据的键
> `<value>`：域中数据键对应的值

``` jsp
<c:set var="<key>" value="<value>" />
```

### 向其他域存入或修改数据

> `<name>`：其他域的名称
>> `page`：pageContext域
>> `resquest`：request域
>> `session`：session域
>> `application`：application域

``` jsp
<c:set var="<key>" value="<value>" scope="<name>" />
```

## 判断语句

### if语句

> `<el>`：利用EL表达式，做判断。如果值为`true`，则输出标签中的内容

``` jsp
<c:if test="<el>">
    ...
</c:if>
```

### choose语句（相当于if else）

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

> `begin`：开始下标
> `end`：结尾下标
> `var`：指定的变量
> `step`：步进数，默认为1

``` jsp
<c:forEach begin="" end="" var="" step="">
    ...
</c:forEach>
```

### 迭代的方式

> `items`：通过EL表达式，指定需要遍历的数组或集合
> `var`：指定的变量

``` jsp
<c:forEach items="" var="">
    ...
</c:forEach>
```

#### 当前遍历状态

> `varStatus`：当前遍历状态
>> `count`：返回当前是第几次遍历，从1开始
>> `first`：只有第一次遍历返回true
>> `last`：只有最后一次遍历返回true

``` jsp
<c:forEach items="" var="" varStatus="vs">
    ${vs.count}
    ${vs.first}
    ${vs.last}
    ...
</c:forEach>
```

## 完成

