---
title: 【笔记】在MacOS系统上制作Windows系统安装盘
date: 2019-11-14 16:57:31
tags:
categories:
- MacOS
---

## 前言

本篇介绍在MacOS系统上，利用命令行，制作Microsoft原版的Windows系统安装盘

<!-- more -->

## 准备工作

- 32G U盘

- [Microsoft原版的Windows系统映像](https://www.microsoft.com/zh-cn/software-download/)

## 开始制作

- 插入U盘，进入"终端"，并查看U盘挂载点名称

``` bash
diskutil list
```

- 通常情况下是最后一个，例如我的是"disk3"

![01.png](/images/20191114165731/01.png)

- 根据自己的U盘挂载点名称，格式化U盘，将U盘命名为"WINDOWS10"

``` bash
diskutil eraseDisk MS-DOS "WINDOWS10" MBR disk3
```

- 在"访达"打开下载好的".iso"系统映像文件，查看映像挂载点名称，例如我的映像挂载点名称为"CES_X64FREV_ZH-CN_DV5"

![02.png](/images/20191114165731/02.png)

- 将映像内的所有文件复制到U盘

``` bash
cp -rp /Volumes/CES_X64FREV_ZH-CN_DV5/* /Volumes/WINDOWS10/
```

- 等待终端再一次出现前缀，表示复制完成

![03.png](/images/20191114165731/03.png)

## 完成

![04.png](/images/20191114165731/04.png)

## 参考文献

[Great Scott——MCFLY WENG](https://mcfly.cn/make-windows-installation-drive-on-mac/)
