---
title: 【笔记】刷入 LineageOS Android 系统
date: 2019-11-21 18:49:16
tags:
categories:
- Android Play Machine
---

## 前言

LineageOS是一个面向智能手机和平板电脑的自由、免费、开放源代码的Android系统分支。它是深受欢迎的定制ROM CyanogenMod的继任者。它在2016年12月Cyanogen公司突然宣布停止开发并关闭项目基础设施后复刻而生。（[维基百科](https://zh.wikipedia.org/wiki/LineageOS)）

我用的手机为二手"Samsung Galaxy S5（中国移动定制版三星系统）"，数据线为"公牛安卓数据线"，电脑系统为MacOS，刷机后手机系统"lineage 16.0 20191120（LineageOS系统）"，初始安卓版本"Android 6.0.1"，刷机后安卓版本"Android 9"

<!-- more -->

<font color="red">警告：本文仅为成功案例分享，出现任何问题后果自负</font>

## 准备工作（续）

- [lineage-16.0-20191120-nightly-kltechn-signed.zip](https://download.lineageos.org/kltechn)（LineageOS三星S5版系统ROM包）

## 开始刷机

### 后接上文

- [传送门](https://feiju12138.github.io/2019/11/20/Android-刷机_1/)

### 刷入第三方Recover（TWRP——另一种方法）

- 使用"fastboot"工具在Fastboot模式刷入TWRP

``` bash
fastboot flash recovery twrp-3.0.2-1-kltechn.img.tar
```

### 刷入系统

- 进入TWRP，"双清"

[传送门](https://feiju12138.github.io/2019/11/20/Android刷机_1/#“双清”)

- "线"刷

[传送门](https://feiju12138.github.io/2019/11/20/Android刷机_1/#“线”刷)

``` bash
adb sideload lineage-16.0-20191120-nightly-kltechn-signed.zip
```

#### 踩坑

- 报错：unknown command log error 7

- 将".zip"系统映像文件解压，修改"updater-script"

``` bash
vim lineage-16.0-20191118-nightly-klte-signed/META-INF/com/google/android/updater-script
```

- 删除"ui_print"前的检查代码,保存并退出

![01.png](/images/20191121184916/01.png)

- 重新打包"lineage-16.0-20191118-nightly-klte-signed"文件夹根目录下的所有文件

![02.png](/images/20191121184916/02.png)

## 完成

- 刷机成功后，首次启动手机会非常慢。

- 展示一张刷机完成的照片，留作纪念。

![03.png](/images/20191121184916/03.png)

## 参考文献

[LineageWiki](https://wiki.lineageos.org/devices/klte)

[YouTuBe——Meteorite Theory](https://www.youtube.com/watch?v=Q6F1AlWRIs0)

[YouTuBe——Mayank Shekhar](https://www.youtube.com/watch?v=h5Kp_jybnjQ)

[YouTuBe——Daze One](https://www.youtube.com/watch?v=E9rvOJemsAc)

