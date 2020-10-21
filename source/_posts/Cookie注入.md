---
title: 【笔记】Cookie 注入
categories:
  - Penetration Tests
date: 2020-03-28 09:38:59
---

## 前言

由于SQL注入可能会被拦截，可以尝试采用Cookie注入的方式渗透测试

<font color="red">本文仅用于网络信息防御学习</font>

<!-- more -->

## 准备工作

- Chrome插件-[ModHeader](https://chrome.google.com/webstore/detail/modheader/idgpnmonknjnojddfkpgkljpfnnfcklj)

## Cookie注入

- 在ModHeader点击加号->选择`Resquest header`->新建一条Cookie，Name="Cookie"，Value="id=1"

![01.png](/images/20200328093859/01.png)

- 刷新网页，查看渗透效果

## Cookie注入方法执行SQL语句

- 需要将SQL语句中的空格替换为`+`

## 完成

## 参考文献

[哔哩哔哩——腾讯掌控安全学院](https://www.bilibili.com/video/BV1qt41157pF)

