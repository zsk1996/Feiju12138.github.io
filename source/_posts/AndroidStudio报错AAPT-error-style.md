---
title: '【踩坑】Android Studio 报错 AAPT: error: style ...'
categories:
  - Android
date: 2020-07-07 12:20:10
---

## 前言

Android Studio 报错：`AAPT: error: style attribute 'android:attr/keyboardNavigationCluster' not found.`

<!-- more -->

## 原因

- 新版本`Gradle`和旧版本`SDK`不兼容导致的各种资源找不到

## 解决问题

- 更换新版本SDK（或降低旧版本`Gradle`）

## 完成

## 参考文献

[CSDN——Everbrilliant89](https://blog.csdn.net/wangyongyao1989/article/details/81737286)

