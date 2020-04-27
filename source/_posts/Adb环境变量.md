---
title: 【笔记】Adb 环境变量（MacOS篇）
date: 2019-12-23 17:00:05
tags:
categories:
- Android
---

## 前言

在终端出现`Command not found`时，通常为没有配置环境变量，本篇为MacOS下配置`adb`环境变量

<!-- more -->

## 打开 .bash_profile 文件

- 使用任意编辑器，打开`~/.bash_profile`文件

``` bash
vim ~/.bash_profile
```

## 编辑 .bash_profile 文件

- 追加环境变量

> `<path>`：软件存放路径

``` bash
export ANDROID_HOME=<path>
export PATH=${PATH}:${ANDROID_HOME}/tools
export PATH=${PATH}:${ANDROID_HOME}/platform-tools
```

## 更新环境变量

``` bash
source ~/.bash_profile
```

## 完成

## 参考文献

[CSDN——tinyvampirepudge](https://blog.csdn.net/qq_26287435/article/details/81513649)

