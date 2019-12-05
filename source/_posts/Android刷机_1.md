---
title: 【笔记】Android 刷机（Flyme篇）
date: 2019-11-20 20:36:32
tags:
categories:
- 刷机
---

## 前言

记一次安卓手机刷机过程。

我用的手机为二手"Samsung Galaxy S5（中国移动定制版三星系统）"，数据线为"公牛安卓数据线"，电脑系统为Windows和MacOS，刷机后手机系统"Flyme 6.7.12.29R beta（魅族系统）"，初始和完成安卓版本"Android 6.0.1"

<!-- more -->

<font color="red">警告：本文仅为成功案例分享，出现任何问题后果自负</font>

## 准备工作

- [SAMSUNG_USB_Driver_for_Mobile_Phones.exe](https://developer.samsung.com/galaxy/others/android-usb-driver-for-windows)（三星手机驱动Windows版）

- [SmartSwitch4Mac_setup.dmg](https://www.samsung.com/cn/apps/smart-switch/)（三星手机S换机助手Mac版）

- [samsung_scl23_scl23_mmb29m.scl23kdu1dqa4_recovery.tar.md5](http://bbs.gfan.com/android-8265909-1-1.html)（三星原版Recovery）

- [twrp-3.0.2-1-kltechn.img.tar](https://dl.twrp.me/kltechn/)（TWRP第三方Recovery）

- [flyme_SM-G9008W_ddfzl_6.7.12.29R-beta.zip](https://www.flyme.cn/firmwarelist-128.html)（Flyme三星S5版魅族系统映像）

- [SDK Platform Tools](https://www.droidviews.com/download-latest-adb-and-fastboot-sdk-platform-tools-win-mac-linux/)（adb工具包）

- 三星SD卡（如果卡刷）

## 开始刷机

### 分别在Windows系统和MacOS系统安装驱动

- Windows

![01.png](/images/20191120203632/01.png)

- MacOS

![02.png](/images/20191120203632/02.png)

### 解锁BootLock

此处略过，因为三星S5默认没有开启BL锁

### 刷入第三方Recovery（TWRP）

#### 手机进入Fastboot（挖煤模式）

- 按住"音量-"+"Home"+"关机"

![03.png](/images/20191120203632/03.png)

- "音量+"确认

![04.png](/images/20191120203632/04.png)

#### 刷入第三方TWRP

- Windows系统打开"Odin 3"软件

- 手机数据线连接电脑

- Odin 第一列 第三行 颜色变化，表示连接成功

- 点击"AP"，选择"TWRP"第三方Recovery，选择"Start"

此过程可能会失败，如遇失败，请刷回三星原厂Recovery

- 待手机进度条满，手机会自动重启

- 重启时按住"音量+"+"Home"+"开机键"进入Recovery模式

![05.png](/images/20191120203632/05.png)

![06.png](/images/20191120203632/06.png)

- 首次进入TWRP需要设置语言为"Chinese（Simplified）"

### 刷入系统

#### "双清"

- 选择"清除"

- 选择"高级清除菜单"

![07.png](/images/20191120203632/07.png)

- 选择除"SD卡"和"USB Storage"以外的所有文件夹

- 滑动确认删除

![08.png](/images/20191120203632/08.png)

- 左下角返回

- 选择"格式化 Data 分区"

![09.png](/images/20191120203632/09.png)

- 输入"yes"，确定

![10.png](/images/20191120203632/10.png)

#### "卡"刷（可选）

- 将Flyme系统映像放在SD卡根目录

- 在TWRP首页选择"安装"

![11.png](/images/20191120203632/11.png)

- 选择"选择存储器"->"SD卡"

![12.png](/images/20191120203632/12.png)

- 选择".zip"Flyme系统映像->"滑动确认刷入"

![13.png](/images/20191120203632/13.png)

#### "线"刷

- Mac使用HomeBrew下载"android-platform-tools"

``` bash
brew cask install android-platform-tools
```

- 在TWRP首页选择"高级"

![14.png](/images/20191120203632/14.png)

- 选择"ADB线刷"

![15.png](/images/20191120203632/15.png)

- 使用终端命令线刷

``` bash
/Users/hatsunemiku/Library/Android/sdk/platform-tools/adb sideload /Users/hatsunemiku/Downloads/flyme_SM-G9008W_ddfzl_6.7.12.29R-beta.zip
```

## 成功

- 刷机成功后，首次启动手机会非常慢。

- 展示一张刷机成功的照片，留作纪念。

![16.png](/images/20191120203632/16.png)

## 参考文献

[CSDN——henauchin](https://blog.csdn.net/sinat_29315697/article/details/79665665)

