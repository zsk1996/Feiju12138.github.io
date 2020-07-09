---
title: 【踩坑】Android Studio 报错：platform 'android-29' not found.
categories:
  - Android
date: 2020-07-07 09:36:44
---

## 前言

Android Studio 报错：`Module 'app': platform 'android-29' not found.`

<!-- more -->

## 原因

- SDK版本选择有误

## 解决问题

- `File`->`Project Structure`->`Modules`->`app`->修改`Compile Sdk Version`的值为已有的值

## 参考文献

[简书——Crazy贵子](https://www.jianshu.com/p/2d70ebd6bf9c)

