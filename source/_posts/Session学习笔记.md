---
title: 【笔记】Session学习笔记
categories:
  - Java
date: 2020-05-13 10:39:12
---

## 前言

Session：在计算机中，尤其是在网络应用中，称为“会话控制”。Session对象存储特定用户会话所需的属性及配置信息。这样，当用户在应用程序的Web页之间跳转时，存储在Session对象中的变量将不会丢失，而是在整个用户会话中一直存在下去。当用户请求来自应用程序的 Web页时，如果该用户还没有会话，则Web服务器将自动创建一个 Session对象。当会话过期或被放弃后，服务器将终止该会话。Session 对象最常见的一个用法就是存储用户的首选项。例如，如果用户指明不喜欢查看图形，就可以将该信息存储在Session对象中。有关使用Session 对象的详细信息，请参阅“ASP应用程序”部分的“管理会话”。注意会话状态仅在支持cookie的浏览器中保留。（[百度百科](https://baike.baidu.com/item/Session/479100)）

用Javaweb实现Session

<!-- more -->

## 获取Session对象

- 因为Session是服务器自动创建的，所以不需要创建Session对象

``` java
HttpSession session = req.getSession();
```

### 重载方法

- 如果有，则返回Session对象
- 如果没有，则创建并返回Session对象

``` java
HttpSession session = req.getSession(true);
```

- 如果有，则返回Session对象
- 如果没有，则返回null值

``` java
HttpSession session = req.getSession(false);
```

## 查看Session编号

``` java
session.getID();
```

## 写入Session数据

- Session是以键值对的形式存入的

> `<key>`：键，String类型
> `<value>`：值，Object类型

``` java
session.setAttribute("<key>", "<value>");
```

## 读取Session数据

- 返回Object类型

``` java
session.getAttribute("<key>");
```

## 设置Session有效期

- Session有效期默认30分钟。如果值为-1，则为永不过期（浏览器未关闭的情况下）

> `<num>`：单位：秒

``` java
session.setMaxInactiveInterval(<num>);
```

### 统一设置Session有效期

- 在web.xml配置Session有效期

``` xml
<session-config>
    <session-timeout><num></session-timeout>
</session-config>
```

## 销毁Session

### 超时销毁

- 默认情况下，当超过30分钟没有访问session，session就会超时销毁。（30分钟是默认时间，可以修改，但不推荐修改）

### 自杀

- 调用session的invalidate方法时，会立即销毁session

``` java
session.invalidate();
```

### 意外身亡

- 当服务器非正常关闭时（硬件损坏，断电，内存溢出等导致服务器非正常关闭），session会随着服务器的关闭而销毁

### 特殊情况

- 当服务器正常关闭，在关闭之前，服务器会将内部的session对象序列化保存到服务器的work目录下，变为一个文件。这个过程叫做session的钝化（序列化）；再次将服务器启动起来，钝化着的session会再次回到服务器，变为服务器中的对象，这个过程叫做session的活化（反序列化）。

## 完成

