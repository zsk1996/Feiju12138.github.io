---
title: 【骚操作】破解 CentOS Linux 开机密码
categories:
  - Linux
date: 2020-06-09 16:33:17
---

## 前言

破解RedHat系列Linux开机密码

<!-- more -->

## 修改启动参数

- 开机后，在进入登录界面前的命令行界面时，按`e`键进入启动参数编辑界面

- 将光标移到`linux16 /vmlinuz ...`行，在末尾追加` rd.break console=tty0`

![01.png](/images/20200609163317/01.png)

- `ctrl`+`x`保存并退出

## 修改新密码

> `<password>`：新密码

``` sh
mount -o remount,rw /sysroot
chroot /sysroot/
echo <password> | passwd --stdin root
touch /.autorelabel
exit
```

![02.png](/images/20200609163317/02.png)

## 完成

- 重启系统

``` sh
reboot
```

