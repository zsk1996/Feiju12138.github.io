---
title: 【踩坑】Unable to access Android SDK add-on list 报错问题
date: 2019-11-17 21:02:17
tags:
categories:
- Android
---

## 前言

首次安装"Android Studio"会报"Unable to access Android SDK add-on list"的问题，原因是首次打开 Android Studio 会自动联网检测 Android SDK 及更新，但是国内会被"墙"，所以可以通过修改"idea.properties"文件跳过联网检测

<!-- more -->

## 修改"idea.properties"文件

- 在Mac下打开"终端"

``` bash
vim /Applications/Android\ Studio.app/Contents/bin/idea.properties
```

- 在末行追加跳过检测命令

``` bash
disable.android.first.run=true
```

## 完成

## 参考文献

[CSDN——又双叒叕](https://blog.csdn.net/u014471160/article/details/78505653)

