---
title: 【骚操作】Android上 安装 Ubuntu 桌面系统
date: 2019-12-14 00:01:07
tags:
---

## 前言

由于安卓是基于Linux二次开发的手机系统,也是支持Linux指令的,通过使用命令行可以完美运行Linux指令，通过指令安装Ubuntu桌面系统XFCE

<!-- more -->

## 准备工作

- Termux

## 安装系统

- 在`Termux`执行命令，安装系统

``` bash
pkg install wget openssl-tool proot -y && hash -r && wget https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/Installer/Ubuntu/ubuntu.sh && bash ubuntu.sh
```

- 进入Ubuntu终端

``` bash
./start-ubuntu.sh
```

- 更新源

``` bash
apt-get update
```

- 安装`wget`工具

``` bash
apt-get install wget -y
```

## 安装桌面

``` bash
wget https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/de-apt-xfce4.sh && bash de-apt-xfce4.sh
```

- 选择语言->`31`

- 选择键盘->`1`

- 设置`vnc`密码

## 远程操控

- 启动`vnc`

``` bash
vncserver-start
```

- 使用`vnc`远程连接

[传送门](https://feiju12138.github.io/2019/12/13/VNC学习笔记/#Android-远程连接-MacOS)

- 在`Address`输入本地ip，端口为5901

`127.0.0.1:5901`

## 完成

## 参考文献

[洋城才子的博客](https://blog.yangchengcaizi.cn/atmx/)

