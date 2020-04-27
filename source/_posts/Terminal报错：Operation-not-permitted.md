---
title: 【踩坑】Terminal 报错：Operation not permitted
categories:
  - MacOS
date: 2020-04-15 10:56:36
---

## 前言

当执行`将ios备份移动到外接硬盘`时，无论是否以root身份，终端都报错：`Operation not permitted`

<!-- more -->

![01.png](/images/20200415105636/01.png)

## 原因

- 终端没有`完全磁盘访问`权限

## 解决问题

- 打开`系统偏好设置`->`安全与隐私`->`隐私`->`完全磁盘访问权限`

- 左下角解锁->点击加号->将`终端`加入其中

![02.png](/images/20200415105636/02.png)

## 完成

## 参考文献

[YouTube——FREE VBA TIPS](https://www.youtube.com/watch?v=wSO02YvnYLg)

