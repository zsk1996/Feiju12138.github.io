---
title: 【笔记】多重引导刷入 Android 双系统
date: 2019-12-22 19:55:17
tags:
categories:
- Android Play Machine
---

## 前言

通过多重引导（Dual Boot Patcher）刷入Android双系统

<!-- more -->

## 准备工作

- 两种ROM刷机包

我使用的分别是

> 魔趣——主系统（[传送门](https://feiju12138.github.io/2019/12/22/刷入魔趣Android系统/)）
> MIUI——副系统（[传送门](https://feiju12138.github.io/2019/12/22/刷入MIUIAndroid系统/)）

- [`Dual Boot Patcher`安装包](https://androidfilehost.com/?fid=385035244224388624)

## 刷入主系统

- 首先通过adb刷入主系统

[传送门](https://feiju12138.github.io/2019/12/22/刷入魔趣Android系统/#开始刷机)

## 为副系统ROM包打补丁

### 安装 Dual Boot Patcher

![01.png](/images/20191222195517/01.png)

### 获取 Root 权限

- 在菜单选择`ROMs`

![02.png](/images/20191222195517/02.png)

- 获取成功后，显示当前只有一个主系统

![03.png](/images/20191222195517/03.png)

### 为副系统ROM包打补丁

- 在菜单选择`Patch Zip File`

- 点击加号选择需要打补丁的系统ROM包

![04.png](/images/20191222195517/04.png)

- 设置参数->`continue`

> `Device`：klet（选择手机型号）
> `Partition configuration`：Data slot（刷入Data分区）->miui（设置名称）

- 选择打补丁后的ROM存储位置及名称

为了区分，我在原名称后添了`2`

![05.png](/images/20191222195517/05.png)

- 开始打补丁

![06.png](/images/20191222195517/06.png)

## 刷入副系统

- 进入`TWRP`Recovery模式

- 选择`高级`->选择`ADB线刷`

``` bash
adb sideload MIUI2_G900F_6.12.27_6.0.1.zip
```

- 重启后自动进入新系统

## 系统切换

- 在新系统同样安装`Dual Boot Patcher`

- 在菜单选择`ROMs`

- 选择下次开机要启动的系统

![07.png](/images/20191222195517/07.png)

## 完成

## 参考文献

[哔哩哔哩——FantWu](https://www.bilibili.com/video/av9551905/)

