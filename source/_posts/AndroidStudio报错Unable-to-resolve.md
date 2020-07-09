---
title: 【踩坑】Android Studio 报错 Unable to resolve ...
categories:
  - Android
date: 2020-07-07 10:07:35
---

## 前言

Android Studio 报错：`Unable to resolve dependency for ':app@debugUnitTest/compileClasspath': Could not resolve androidx.constraintlayout:constraintlayout:1.1.3.`

<!-- more -->

## 原因

- `Android Studio`版本太高，而`Gradle`为低版本

## 解决问题

- 升级`Gradle`

``` sh
brew upgrade gradle
```

## 完成

## 参考文献

[CSDN——LVXIANGAN](https://blog.csdn.net/LVXIANGAN/article/details/84860691)

