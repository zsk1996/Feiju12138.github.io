---
title: 【笔记】刷入 EdXposed
categories:
  - Android Play Machine
date: 2020-03-12 15:58:16
---

## 前言

Xposed作为安卓上有名的框架，在高权限模式下运行，在不修改程序的情况，影响程序使用的一套框架。不过由于revo一直不更新Xposed，而Android 10都快到来了，所以民间高手推出了EdXposed框架来代替Xposed。

<!-- more -->

## 准备工作

- Magisk刷机包[传送门](https://github.com/topjohnwu/Magisk/releases)

- MagiskManager安装包[传送门](https://github.com/topjohnwu/Magisk/releases)

- MagiskRiruCore刷机包[传送门](https://github.com/RikkaApps/Riru/releases)

- EdXposed刷机包[传送门](https://github.com/ElderDrivers/EdXposed/releases)

- EdXposedManager安装包[传送门](https://github.com/ElderDrivers/EdXposedManager/releases)

## 刷入Migisk

- 进入Recovery模式->高级->ADB线刷

``` sh
adb sideload /Users/hatsunemiku/Downloads/Magisk-v20.3.zip
```

- 完成后重启进入系统

### 安装MisgiskManager

``` sh
adb install /Users/hatsunemiku/Downloads/MagiskManager-v7.5.1.apk
```

## 刷入MagiskRiruCore

- 进入Recovery模式->高级->ADB线刷

``` sh
adb sideload /Users/hatsunemiku/Downloads/magisk-riru-core-v19.7.zip
```

- 完成后重启进入系统

## 刷入EdXposed

- 进入Recovery模式->高级->ADB线刷

``` sh
adb sideload /Users/hatsunemiku/Downloads/EdXposed-SandHook-v0.4.6.1.4510.-release.zip
```

- 完成后重启进入系统

### 安装EdXposedManager

``` sh
adb install /Users/hatsunemiku/Downloads/EdXposedManager-4.5.4-45401-org.meowcat.edxposed.manager-release.apk
```

## 完成

## 参考文献

[XZYMOE的博客](https://www.xzymoe.com/android-9-flash-xposed/)

