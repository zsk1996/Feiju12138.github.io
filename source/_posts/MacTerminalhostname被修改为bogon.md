---
title: 【踩坑】Mac Terminal hostname 被修改为 bogon
categories:
  - MacOS
date: 2020-01-26 16:53:51
---

## 前言

修复`Mac Terminal`的`hostname`被修改的`bogon`

<!-- more -->

![01.png](/images/20200126165351/01.png)

## 原因

- `DNS`服务器地址被修改

## 解决问题

- 打开系统偏好设置

- 选择`网络`

![02.png](/images/20200126165351/02.png)

- 选择`高级`

![03.png](/images/20200126165351/03.png)

- 选择`DNS`

![04.png](/images/20200126165351/04.png)

- 添加`DNS服务器`

![05.png](/images/20200126165351/05.png)

- 输入`8.8.8.8`->`好`

![06.png](/images/20200126165351/06.png)

- 选择`应用`

![07.png](/images/20200126165351/07.png)

## 完成

- `Terminal`恢复

![08.png](/images/20200126165351/08.png)

## 参考文献

[知乎——Bgwan](https://zhuanlan.zhihu.com/p/55827741)

