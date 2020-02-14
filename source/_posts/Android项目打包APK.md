---
title: 【笔记】Android 项目打包 APK
categories:
  - Android
date: 2020-02-14 23:18:22
---

## 前言

将`Android项目`打包为`APK安装包`文件

<!-- more -->

## 打包未签名 APK 文件

- 在`Android Studio`菜单栏选择`Build`->`Build Bundle(s)/APK(s)`->Build APK(s)

![01.png](/images/20200214231822/01.png)

- 打包后的APK文件为`/app/build/outputs/apk/debug`目录下的`/app-debug.apk`文件

## 打包签名 APK 文件

### 选择打包为 APK

- 在`Android Studio`菜单栏选择`Build`->`Generate Signed Bundle/APK...`

![02.png](/images/20200214231822/02.png)

- 勾选`APK`->`Next`

![03.png](/images/20200214231822/03.png)

### 新建签名文件（可选）

- 选择`Create new...`新建签名文件

![04.png](/images/20200214231822/04.png)

> `Key store path`：设置签名文件存放路径
> `Password`：设置文件密码
> `Confirm`：重复文件密码
>> `Key`：设置签名信息
>> `Alias`：设置别名
>> `Password`：设置密码
>> `Confirm`：重复密码
>> `Validity`：有效年限
>>> `Certificate`：设置开发者信息（至少填一项）

![05.png](/images/20200214231822/05.png)

- `OK`

### 配置签名

> `Key store path`：签名存放路径
> `Key store password`：签名文件密码
> `Key alias`：别名
> `Key password`：密码

![06.png](/images/20200214231822/06.png)

- `Next`

### 生成 APK

- `Build Variants`分别为`debug`APK（测试安装包）和`release`APK（发行版安装包），根据需求选择

- `Signature Versions`至少选择一项，区别：

V1：仅验证未解压的文件内容，这样APK签署后可进行许多修改 ，可以移动甚至重新压缩文件
V2：验证压缩文件的所有字节，而不是单个ZIP条目，因此，在签名后无法再更改(包括zipalign)。正因如此，现在在编译过程中，我们将压缩、调整和签署合并成一步完成。好处显而易见，更安全而且新的签名可缩短在设备上进行验证的时间（不需要费时地解压缩然后验证），从而加快应用安装速度。但如有任何自定义任务篡改APK文件或对其进行后处理（无论以任何方式），那么V2 签名会有作废的风险，从而导致您的 APK 与 Android 7.0 及更高版本不兼容

|Android 版本|V1|V2|V1 & V2|
|---|---|---|---|
|7.0及以上系统|安装成功|安装成功|安装成功|
|7.0以下版本|安装成功|安装失败|安装成功|

![07.png](/images/20200214231822/07.png)

- `Finish`

## 完成

## 参考文献

[CSDN——qq_32611951](https://blog.csdn.net/qq_32611951/article/details/80505786)
[CSDN——HUandroid](https://blog.csdn.net/huandroid/article/details/79012599)

