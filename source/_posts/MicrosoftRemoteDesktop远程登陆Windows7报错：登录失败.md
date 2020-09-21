---
title: 【踩坑】Microsoft Remote Desktop 远程登陆 Windows7 报错：登录失败
categories:
  - MacOS
date: 2020-09-08 08:53:03
---

## 前言

`Microsoft Remote Desktop`远程登陆`Windows7`报错：`登录失败：用户账户限制。可能的原因包括不允许空密码，登陆时间限制，或强制的策略限制。`

<!-- more -->

## 报错原因

- 无密码远程登陆Windows7

## 解决问题

- 为账户设置密码或修改权限

### 修改权限

- 通过`运行`打开组策略编辑器

``` sh
gpedit.msc
```

- `计算机配置`->`Windows设置`->`安全设置`->`本地策略`->`安全选项`

- 将`账户：使用空密码的本地账户只允许进行控制台登陆`改为`已禁用`

## 完成

## 参考文献

[SCDN——柳旭辉](https://blog.csdn.net/xuhui_liu/article/details/73832743)

