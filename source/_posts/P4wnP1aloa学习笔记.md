---
title: 【笔记】P4wnP1 aloa 学习笔记
categories:
  - Raspberry Pi
date: 2020-01-16 22:54:52
---

## 前言

P4wnP1 A.L.O.A. by MaMe82 is a framework which turns a Rapsberry Pi Zero W into a flexible, low-cost platform for pentesting, red teaming and physical engagements ... or into "A Little Offensive Appliance".（[官网](https://github.com/mame82/P4wnP1_aloa)）

<!-- more -->

## 准备工作

- [kali-linux-v0.1.0-alpha2-rpi0w-nexmon-p4wnp1-aloa.img](https://github.com/mame82/P4wnP1_aloa/releases)

## 安装

- 直接将`p4wnp1-aloa.img`烧录到树莓派

## 启动方法

- 连接wifi

> 名称：`💥🖥💥p4wnp1`
> 密码：`MaMe82-P4wnP1`

- 登陆浏览器

> 网址：`172.24.0.1:8000`

- 登录ssh

> ip地址：`172.24.0.1`
> 端口号：`22`
> 用户名：root
> 密码：toor

## 格式化一部分伪装U盘

- 登录ssh

- 格式化500M，名称为`sneak`

``` sh
cd /usr/local/P4wnP1/helper/
./genimg -i -s 500 -o 500mb -l sneak
```

![01.png](/images/20200116225452/01.png)

- 登录网页

- 关闭`Mouse`，打开`Mass Storage`

![02.png](/images/20200116225452/02.png)

- 编辑`Mass Storage`->`Image file to use`选择刚刚格式化的`500mb.bin`

![03.png](/images/20200116225452/03.png)

- 选择`DEPLOY`保存设置

![04.png](/images/20200116225452/04.png)

## 运行脚本

- 登录网页，菜单选择`HIDSCRIPT`

![05.png](/images/20200116225452/05.png)

## 自制脚本demo

``` javascript
press("GUI r");
delay(500);
type("shutdown -s -t 60\n");
```

## 参考文献

[YouTuBe——Seytonic](https://www.youtube.com/watch?v=I_BjCdJlCo4)

