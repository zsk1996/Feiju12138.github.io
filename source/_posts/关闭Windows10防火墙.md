---
title: 【笔记】关闭 Windows 10 防火墙
categories:
  - Windows
date: 2020-07-09 19:26:29
---

## 前言

新装的Windows10操作系统，第一步优化就是完全关闭Windows10防火墙

<!-- more -->

## 关闭防火墙程序

- 搜索`防火墙`->打开`Windows Defender 防火墙`

![01.png](/images/20200709192629/01.png)

- 选择`启用或关闭Windows Defender 防火墙`

![02.png](/images/20200709192629/02.png)

- 将`专用网络`和`公用网络`的防火墙均关闭

![03.png](/images/20200709192629/03.png)

- 关闭成功

![04.png](/images/20200709192629/04.png)

## 关闭防火墙服务

- 搜索`运行`->打开`运行`

![05.png](/images/20200709192629/05.png)

- 输入`gpedit.msc`打开组策略编辑器

[Windows10家庭版开启组策略编辑器](/2019/11/02/Windows10家庭版开启组策略/)

![06.png](/images/20200709192629/06.png)

- `计算机配置`->`管理模版` ->`Windows组件`->双击`Microsoft Defender 防病毒`

![07.png](/images/20200709192629/07.png)

- 双击`关闭Microsoft Defender 防病毒`

![08.png](/images/20200709192629/08.png)

- 选择`已启用`->`确定`

![09.png](/images/20200709192629/09.png)

## 完成

## 参考文献

[个人图书馆——智多星dcdcr5sx](http://www.360doc.com/content/17/1213/05/37114935_712575127.shtml)

