---
title: 【踩坑】Atom报错：Cannot load the ...
date: 2019-12-11 11:31:57
tags:
---

## 前言

安装`Atom`后，每次打开，都会报错：`Cannot load the system dictionary for zh-CN. Checked the following paths for dictionary files:`

<!-- more -->

![01.png](/images/20191211113157/01.png)

## 解决问题

- 修改插件`spell-check`的设置

Atom->首选项->扩展->搜索`spell-check`->设置

![02.png](/images/20191211113157/02.png)

- 取消勾选`Use Locales`->在`Locales`填入`en-US`

![03.png](/images/20191211113157/03.png)

## 完成

- 重启`Atom`

## 参考文献

[简书——我要微微辣](https://www.jianshu.com/p/dcb758424e07)

