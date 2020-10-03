---
title: 【骚操作】破解 Kali Linux 开机密码
categories:
  - Linux
date: 2020-09-28 19:52:18
---

## 前言

破解`Kali Linux`开机密码

<!-- more -->

## 修改启动参数

- 开机后，在进入登录界面前的命令行界面时，按e键进入启动参数编辑界面

- 将光标移到`linux /boot ...`行，修改`ro`为`rw`，并将其后所有字符串删除，修改为`init=/bin/bash`

![01.png](/images/20200928195218/01.png)

- `ctrl`+`x`保存并退出

## 修改新密码

``` sh
passwd
```

## 完成

- 重启系统

## 完成

## 参考文献

[CSDN——zhaokaifeng.com](https://blog.csdn.net/wy_bk/article/details/88901882)

