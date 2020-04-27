---
title: 【踩坑】Android Studio 报错："Connection refused (Connection refused)"
date: 2019-11-19 15:54:45
tags:
categories:
- Android
---

## 前言

Android Studio 项目点击运行后，待构建完成，报错："Connection refused (Connection refused)"

解决办法：删除代理设置

<!-- more -->

## 解决问题

- 编辑"gradle.properties"文件

``` bash
vim /Users/(YourName)/.gradle/gradle.properties
```

- 删除代理设置

``` bash
systemProp.http.proxyHost=127.0.0.1
systemProp.http.proxyPort=52909
systemProp.https.proxyHost=127.0.0.1
systemProp.https.proxyPort=52909
```

## 完成

## 参考文献

[简书——flovm](https://www.jianshu.com/p/dc12c965abbc)

