---
title: 【踩坑】解决 jQuery 冲突问题
date: 2019-12-26 16:49:02
tags:
categories:
- jQuery
---

## 前言

`$`作为jQuery的标识符，有可能被其他框架使用，此时为了解决`$`冲突问题，释放`$`使用权

<!-- more -->

## 解决jQuery冲突问题

- 释放后，`$`将不再作为jQuery标识符，只能使用`jQuery`关键字作为jQuery标识符

``` javascript
jQuery.noConflict();
```

## 参考文献

[哔哩哔哩——李南江老师](https://www.bilibili.com/video/av22807707?p=5)

