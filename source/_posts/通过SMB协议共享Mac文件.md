---
title: 【笔记】通过 SMB 协议共享 Mac 文件
categories:
  - MacOS
date: 2019-12-29 14:18:20
---

## 前言

服务器消息块，又称网络文件共享系统，一种应用层网络传输协议，由微软开发，主要功能是使网络上的机器能够共享计算机文件、打印机、串行端口和通讯等资源。它也提供经认证的进程间通信机能。它主要用在装有Microsoft Windows的机器上，在这样的机器上被称为Microsoft Windows Network。（[维基百科](https://zh.wikipedia.org/wiki/伺服器訊息區塊)）

<!-- more -->

## 准备工作

- [ES文件浏览器](http://www.estrongs.com/)

## 操作方法

### MacOS 服务端开启共享

- `系统偏好设置`->`共享`

- 勾选`文件共享`

- 在选项中，勾选`使用SMB来共享文件和文件夹`，勾选账户

![01.png](/images/20191229141820/01.png)

- 查看并记录Mac服务端ip地址

``` sh
ifconfig
```

### MacOS 客户端查看共享

- 在`访达`中 `command`+`k` 打开`连接到服务器`

> `<ip_address>`：Mac服务端ip地址

`smb://<ip_address>`

> 点击`连接`

> 使用Mac服务端用户名密码进行登陆

### Windows 客户端查看共享

- `win`+`r` 打开`运行`

`\\<ip_address>`

- 点击`运行`

- 使用Mac服务端用户名及密码进行登录

### IOS客户端查看共享

- `文件`->`...`->`连接服务器`

`smb://<ip_address>`

- 使用Mac服务端用户名及密码进行登录->`下一步`

### Android 客户端查看共享

- 打开`ES文件浏览器`->左上角菜单->`网络`->`局域网`->`扫描`

- 选择MacOS服务端

- 使用客人用户登录->`确定`

`用户名`为`guest`，`密码`为空

## 完成

## 参考文献

[知乎——麦克叉](https://zhuanlan.zhihu.com/p/69631236)

