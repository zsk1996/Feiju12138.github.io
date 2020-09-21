---
title: 【踩坑】Microsoft Remote Desktop 远程登陆 Windows7 报错：Your session ended
categories:
  - MacOS
date: 2020-09-08 09:01:18
---

## 前言

`Microsoft Remote Desktop`远程登陆`Windows7`报错：`Your session ended because of an error. If this keeps happening, contact your network administrator for assistance.`

<!-- more -->

## 报错原因

- Windows客户端计算机上的最大未完成连接限制有问题

## 解决问题

- 通过`运行`打开注册表编辑器

``` sh
regedit
```

- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server`

- 修改`MaxOutstandingConnections`的值为16进制的`10000`

- 如果没有则创建名为`MaxOutstandingConnections`的`DWORD键`值为16进制的`10000`

## 完成

## 参考文献

[Microsoft Remote Desktop 论坛](https://remotedesktop.uservoice.com/forums/287834-remote-desktop-client-for-mac/suggestions/39105910-your-session-has-ended-because-of-an-error-err)

