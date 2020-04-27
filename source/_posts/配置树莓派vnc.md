---
title: 【笔记】配置 树莓派 vnc
categories:
  - Raspberry Pi
date: 2020-01-13 11:15:53
---

## 前言

通过`vnc`远程连接树莓派桌面

<!-- more -->

## 准备工作

- [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/)

## 配置 vnc

- 通过`ssh`远程连接树莓派

- 打开树莓派配置

``` sh
sudo raspi-config
```

### 开启 vnc 功能

- 选择`5 Interfacing Options`

![01.png](/images/20200113111553/01.png)

- 选择`P3 VNC`

![02.png](/images/20200113111553/02.png)

- `Yes`

![03.png](/images/20200113111553/03.png)

- `Ok`

![04.png](/images/20200113111553/04.png)

### 配置桌面分辨率

- 选择`7 Advanced Options`

![05.png](/images/20200113111553/05.png)

- 选择`A5 Resolution`

![06.png](/images/20200113111553/06.png)

- 选择`DMT Mode 82 1920*1080 60Hz 16:9`

![07.png](/images/20200113111553/07.png)

- `Ok`

![08.png](/images/20200113111553/08.png)

### 重启

- `Finish`

![09.png](/images/20200113111553/09.png)

- `Yes`

![10.png](/images/20200113111553/10.png)

## 远程桌面

- 打开`VNC Viewer`

- 通过IP地址连接树莓派

> `<ip_address>`：ip地址
> `<port>`：端口号

``` sh
<ip_address>:<port>
```

- 输入用户名和密码

> 用户名：pi
> 密码：raspberry

## 完成

![11.png](/images/20200113111553/11.png)

## 参考文献

[哔哩哔哩——jinganwang](https://www.bilibili.com/video/av72048534?p=2)
[CSDN——绝世好阿狸](https://blog.csdn.net/u010900754/article/details/53048998)

