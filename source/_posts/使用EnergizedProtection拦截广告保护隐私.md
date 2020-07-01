---
title: 【骚操作】使用 Energized Protection 拦截广告保护隐私
categories:
  - Android Play Machine
date: 2019-11-23 20:11:25
tags:
---

## 前言

Energized Protection 是一款黑名单整合，可以有效拦截钓鱼网站保护隐私。[github](https://github.com/EnergizedProtection/block)

<!-- more -->

## 准备工作

- Android手机

- Magisk Manager（[传送门](https://feiju12138.github.io/2019/11/21/Android刷机_2/#刷入Magisk获取ROOT权限（可选）)）

- Termux（[传送门](https://feiju12138.github.io/2019/11/22/将安卓手机作为一台服务器/#安装”Termux”)）

## 安装 Energized Protection

- 打开`Magisk Manager`-> 选择`左上角菜单`->选择`下载`

- 搜索`Energized Protection`->安装

### 刷机安装 Energized Protection（可选）

- 由于我的`Magisk Manager`无法安装`Energized Protection`，所以我采用刷机的方式安装

## 启动 Energized Protection

- 打开`Termux`

- 获取管理员权限->启动`Energized Protection`

``` bash
su
energized
```

### 开启`Systemless hosts`权限（踩坑）

- 首次运行前，需前往`Magisk Manager`->`设置`->`Systemless hosts`，开启权限

## 使用 Energized Protection

- 在菜单选择需要安装的包的编号->输入`Y`确认

``` bash
6
Y
```

## 完成

- 重启手机

## 参考文献

[Freedom Wolf](https://www.freedomwolf.cc/2019/04/energized-protection/)

