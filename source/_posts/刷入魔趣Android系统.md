---
title: 【笔记】刷入 魔趣 Android 系统
date: 2019-12-22 19:45:25
tags:
categories:
- Android Play Machine
---

## 前言

魔趣开源项目，前身为魔趣OS，是基于CAF 二次开发的一个Android分支版本，同时也是中国大陆首个完全开源的Android第三方操作系统。 魔趣的所有功能完全遵循Material Design，是一款类原生Android操作系统。（[维基百科](https://zh.wikipedia.org/zh-cn/魔趣)）

<!-- more -->

## 准备工作

- [MK81.0-kltechn-191215-RELEASE.zip](https://download.mokeedev.com)（魔趣三星S5版系统ROM包）

## 开始刷机

- 进入`TWRP`Recovery模式

- 选择`高级`->选择`ADB线刷`

``` bash
adb sideload MK81.0-kltechn-191215-RELEASE.zip
```

### 踩坑

- 和`LineageOS`同样的坑，填坑方法相同

[传送门](https://feiju12138.github.io/2019/11/21/刷入LineageOSAndroid系统/#踩坑)

## 完成

- 刷机成功后，首次启动手机会非常慢。

- 展示一张刷机完成的照片，留作纪念。

![01.png](/images/20191222194525/01.png)

