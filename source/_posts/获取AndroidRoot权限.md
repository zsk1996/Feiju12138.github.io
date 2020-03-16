---
title: 【笔记】获取 Android Root 权限
date: 2019-12-18 20:46:07
tags:
categories:
- 刷机
---

## 前言

为`Lineage OS`系统通过刷机的方式获取`Root`权限

<!-- more -->

## 准备工作

- [addonsu-16.0-arm-signed.zip](https://download.lineageos.org/extras)

- [Magisk-v20.1.zip](https://github.com/topjohnwu/Magisk/releases)

## 通过原生方式

### 刷入 Lineage OS 官方提供的 Root 刷机包

``` bash
adb sideload addonsu-16.0-arm-signed.zip
```

### 获取 Root 权限

- 设置->系统

![01.png](/images/20191218204607/01.png)

- 高级

![02.png](/images/20191218204607/02.png)

- 开发者选项

![03.png](/images/20191218204607/03.png)

- Root授权

![04.png](/images/20191218204607/04.png)

- 应用与ADB

![05.png](/images/20191218204607/05.png)

### 管理 Root 权限

- 管理Root访问

![06.png](/images/20191218204607/06.png)

## 通过 Magisk

### 刷入 Magisk 来获取 Root 权限

``` bash
adb sideload Magisk-v20.1.zip
```

### 获取 Root 权限

- 打开`Magisk Manager`App，显示绿色对勾表示已安装

![07.png](/images/20191218204607/07.png)

### 管理 Root 权限

- `Migisk Manager`菜单->超级用户

![08.png](/images/20191218204607/08.png)

