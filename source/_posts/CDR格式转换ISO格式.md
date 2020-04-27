---
title: 【踩坑】CDR格式 转换 ISO格式
date: 2019-11-09 12:07:05
tags:
categories:
- MacOS
---

## 前言

有段时间学习安装黑苹果系统，在百度上找到很多黑苹果系统映像，其中有一款最适合小白使用，那就是文件名为"macOS Sierra 10.12.6 16G29 Installer.cdr"的懒人版黑苹果系统映像，虽然人们都说".cdr"文件可以直接烧录到U盘，但为了能让烧录更简单，我决定将".cdr"文件转换为常见的系统映像格式".iso"。

<!-- more -->

## 准备工作

- 一个".cdr"文件的黑苹果系统映像
- 一台MacOS系统的电脑

## 打开终端

- 访达->应用程序->实用工具->终端

![01.png](/images/20191109120705/01.png)

## 使用终端，进入存放".cdr"文件的目录

- 由于我的".cdr"文件放在"桌面"目录上，所以在终端执行以下命令

``` bash
cd ~/Desktop/
```

## 修改文件名（可选）

### 为了接下来的转换操作顺利进行，先将文件名修改成"Installer.cdr"（如果会根据自己的文件名修改下一步骤的命令，可以跳过此步骤）

- 右键"macOS Sierra 10.12.6 16G29 Installer.cdr"文件->重新命名

![02.png](/images/20191109120705/02.png)

- 将文件命名为"Installer.cdr"

## 格式转换

- 在终端执行转换命令

``` bash
hdiutil makehybrid -iso -joliet -o Installer.iso Installer.cdr
```

## 完成

## 参考文献

百度
