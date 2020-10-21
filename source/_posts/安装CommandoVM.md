---
title: 【笔记】安装 Commando VM
categories:
  - Penetration Tests
date: 2020-01-09 20:13:14
---

## 前言

Commando VM使用Boxstarter，Chocolatey和MyGet软件包来安装软件，并提供许多工具和实用程序来支持渗透测试。Commando VM拥有170多种工具，并且在不断发展壮大，其目标是成为每个渗透测试人员和红军人员事实上的Windows计算机。（[官网](https://www.fireeye.com/blog/threat-research/2019/08/commando-vm-customization-containers-kali.html)）

<font color="red">本文仅用于网络信息防御学习</font>

<!-- more -->

## 准备工作

- `Windows 7`或`Windows 10`操作系统

## 开始安装

- 推荐使用虚拟机安装

### 下载自动安装脚本

``` sh
git clone https://github.com/fireeye/commando-vm.git
```

### 将脚本复制到 Windows 系统

- 找到文件`install.ps1`，复制到`文档`

### 打开 Windows Powershell

- 在搜索框输入`Windows Powershell`

- 选择`以管理员身份运行`

![01.png](/images/20200109201314/01.png)

### 授予权限

``` sh
Set-ExecutionPolicy Unrestricted
```

- 输入`A`

### 运行安装脚本

``` sh
cd C:\Users\hatsunemiku\Documents\
.\install.ps1
```

### 开始自动安装

![02.png](/images/20200109201314/02.png)

## 完成

- 安装过程中可能会多次重启，属于正常现象

- 展示一张安装完成的截图，留作纪念。

![03.png](/images/20200109201314/03.png)

