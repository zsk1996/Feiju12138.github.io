---
title: 【踩坑】Android Studio 第一次新建项目报4处错误
date: 2019-11-18 18:04:25
tags:
---

## 前言

第一次创建 Android Studio 项目，会报4处错误，原因是有部分Gradle包没有下载下来，通过修改链接解决问题

<!-- more -->

## 解决问题

- 找到"gradle-wrapper.properties"文件

文件的位置为"/gradle/wrapper/gradle-wrapper.properties"

- 修改"gradle-wrapper.properties"文件

将第6行去掉"\\"

``` properties
distributionUrl=https://services.gradle.org/distributions/gradle-5.4.1-all.zip
```

- 重新构建项目

## 完成

## 参考文献

[红黑联盟——JuneCock](https://www.2cto.com/kf/201706/649003.html)

