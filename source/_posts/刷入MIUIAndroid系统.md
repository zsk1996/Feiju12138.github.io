---
title: 【笔记】刷入 MIUI Android 系统
date: 2019-12-22 19:30:24
tags:
categories:
- 刷机
---

## 前言

MIUI是由中国手机厂商小米科技开发的基于Android的二级市场固件，当前最新正式发布版本为MIUI 11。MIUI为小米科技研发的智能手机产品的预装操作系统固件，也有小米官方、部分爱好者基于MIUI Patchrom将该固件移植至其他手机品牌的智能手机上。（[维基百科](https://zh.wikipedia.org/zh-cn/MIUI)）

<!-- more -->

<font color="red">警告：本文仅为成功案例分享，出现任何问题后果自负</font>

## 准备工作

- [MIUI_G900F_6.12.27_6.0.1.zip](https://drive.google.com/file/d/1OLasAyAO7MgIUhO6ErJtQW9KkAqOzkMD/view)（MIUI三星S5版系统ROM包）

## 开始刷机

- 进入`TWRP`Recovery模式

- 选择`高级`->选择`ADB线刷`

``` bash
adb sideload MIUI_G900F_6.12.27_6.0.1.zip
```

## 完成

- 刷机成功后，首次启动手机会非常慢。

- 展示一张刷机完成的照片，留作纪念。

![01.png](/images/20191222193024/01.png)

