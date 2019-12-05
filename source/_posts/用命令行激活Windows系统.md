---
title: 【骚操作】用命令行激活Windows系统
date: 2019-11-14 23:16:31
tags:
categories:
- Windows
---

## 前言

通常情况下，可以在Windows系统的"设置"中激活新的Windows系统，但是总有那么几款Windows在"设置"中找不到"激活"，或者找起来很麻烦，不管什么原因，介绍一种使用命令行激活Windows10的方法

<!-- more -->

## 打开命令行

- 开始->Windows系统->命令提示符（右键）->更多->以管理员身份运行

![01.png](/images/20191114231631/01.png)

## 卸载产品密钥（可选）

- 如果设备已激活，可以通过此命令取消激活

``` bash
slmgr.vbs /upk
```

## 激活Windows10

- 输入激活命令

``` bash
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms zh.us.to
slmgr /ato
```

- 查看产品过期时间

``` bash
slmgr.vbs -xpr
```

## 完成

![02.png](/images/20191114231631/02.png)

## 参考文献

[博客园——我有点帅哦](https://www.cnblogs.com/junjunjun123/p/8548703.html)

