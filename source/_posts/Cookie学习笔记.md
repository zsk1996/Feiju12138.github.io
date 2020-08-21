---
title: 【笔记】Cookie学习笔记
categories:
  - Java
date: 2020-05-13 10:25:08
---

## 前言

Cookie（复数形态Cookies），又称为“小甜饼”。类型为“小型文本文件”，指某些网站为了辨别用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。由网景公司的前雇员卢·蒙特利在1993年3月发明。最初定义于RFC 2109。当前使用最广泛的 Cookie标准却不是RFC中定义的任何一个，而是在网景公司制定的标准上进行扩展后的产物。（[维基百科](https://zh.wikipedia.org/wiki/Cookie)）

用Javaweb实现Cookie

<!-- more -->

## 创建Cookie对象

- Cookie都是由键值对构成的

> `<key>`：键，Cookie的名字，Cookie名字一旦指定无法修改
> `<value>`：值，Cookie要保存的值

``` java
Cookie cookie = new Cookie("<key>", "<value>");
```

## 写入Cookie到客户端

``` java
resp.addCookie(cookie);
```

## 读取Cookie

- 读取到的是Cookie数组

``` java
Cookie cookies[] = req.getCookies();
```

### 获取Cookie的名字

- 返回String类型

``` java
cookie.getName();
```

### 获取/修改Cookie的值

- 返回String类型

``` java
cookie.getValue();
cookie.setValue();
```

## 设置Cookie有效期

> `<num>`：单位：秒
>> `正数`：设置Cookie有效期（存储在硬盘上）
>> `负数`：默认值，Cookie只在关闭浏览器之前有效（存储在浏览器缓存）
>> `0`：立即删除同名Cookie

``` java
cookie.setMaxAge(<num>);
```

## Cookie的注意事项

- Cookie存储的数据保存在客户端
- 单个Cookie大小不能超过4kb
- 一个域名最多可以往一个客户端写20个Cookie

- Cookie只能存放安全性要求不高的信息，比如密码等信息不能直接保存在Cookie
- 不同浏览器读取不同的Cookie

## 参考文献

达内教育

