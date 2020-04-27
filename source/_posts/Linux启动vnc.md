---
title: 【进阶】Linux 启动 vnc
categories:
  - Linux
date: 2020-01-14 20:46:48
---

## 前言

VNC，为一种使用RFB协议的屏幕画面分享及远程操作软件。此软件借由网络，可发送键盘与鼠标的动作及即时的屏幕画面。 VNC与操作系统无关，因此可跨平台使用，例如可用Windows连线到某Linux的电脑，反之亦同。甚至在没有安装客户端程序的电脑中，只要有支持JAVA的浏览器，也可使用。（[维基百科](https://zh.wikipedia.org/wiki/VNC)）

<!-- more -->

## 启动 vnc

### 安装 vnc 服务端

``` sh
sudo apt-get install tightvncserver
```

### 启动 vnc 服务端

``` sh
vncserver
```

## 完成

![01.png](/images/20200114204648/01.png)

## 参考文献

[CSDN——Lyh-Memory](https://blog.csdn.net/u012313335/article/details/73912556)

