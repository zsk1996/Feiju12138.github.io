---
title: 【笔记】安装 Android-x86 系统
date: 2019-12-26 13:40:24
tags:
categories:
- System Installation
---

## 前言

Android-x86是基于开源的谷歌Android移动操作系统开发的衍生版本，目标硬件平台为x86处理器，而不是基于RISC的ARM芯片。该项目自2009年创立，至今已超过十年，并派生出更多版本，比如Remix OS和Phoenix OS。 官方网站： Android-x86。（[维基百科](https://zh.wikipedia.org/zh-cn/Android-x86)）

`Android-x86`系统安装过程，系统版本`64位 Android 9.0`

<!-- more -->

## 开始安装

- 插入U盘，开机进入BIOS启动`Android-x86`系统安装盘

- 选择第三行`Android-x86 9.0-rcl Installation`

## Choose Partition

- 选择一块分区作为`Android-x86`系统盘

## Choose filesystem

- 选择任意文件格式

`ext4`

## Confirm

- 提醒格式化将会丢失数据，选择`Yes`

## Confirm

- 是否安装EFI引导，选择`Yes`

## Question

- 是否安装`/system`目录作为读写区，选择`Yes`

## Installing Android-x86 to sda13

- 开始安装，全程自动安装，无需人工操作

## Congratulations

- 安装完成，直接启动`Android-x86`，选择`Run Android-x86`

## 完成

