---
title: 【笔记】在 Android 手机安装 JDK
categories:
  - Android Play Machine
date: 2020-02-10 00:51:25
---

## 前言

在`Android`手机安装`JDK`

<!-- more -->

## 准备工作

- 安装`Termux.app`

## 安装 Arch Linux

[传送门](https://feiju12138.github.io/2020/02/11/Termux安装ArchLinux/)

## 更换 Arch Linux 更新源

[传送门](https://feiju12138.github.io/2020/02/11/更换ArchLinux更新源/)

## 安装 jdk

- 使用ArchLinux的软件包管理器`pacman`安装`jdk`

``` sh
pacman -Syy; pacman -Su; pacman -S jdk8-openjdk
```

- 安装过程中两次询问是否继续，输入`Y`确认

## 完成

- 查看jdk版本号

``` sh
java -version
```

![01.png](/images/20200210005125/01.png)

## 参考文献

[GitHub——SDRausty](https://github.com/termux/termux-app/issues/397)

