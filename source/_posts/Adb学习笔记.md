---
title: 【笔记】Adb 学习笔记
date: 2019-12-22 21:02:57
tags:
categories:
- Android Play Machine
---

## 前言

Android调试桥，是一种拥有许多功能的命令行工具，可让您与设备进行通信。ADB命令便于执行各种设备操作（例如安装和调试应用，传输文件等），并提供对Unix shell（可用来在设备上运行各种命令）的访问权限。它是一种客户端-服务器程序，包括客户端、守护进程（adbd）、服务器三个组件。（[维基百科](https://zh.wikipedia.org/wiki/Android调试桥)）

<!-- more -->

## 基本命令

### 查看adb的版本信息

``` bash
adb version
```

### 启动adb

``` bash
adb start-server
```

### 停止adb

``` bash
adb kill-server
```

### 以root权限运行adb

``` bash
adb root
```

### 指定adb server的网络端口

- adb默认端口为5037

``` bash
adb -P <port> start-server
```

### 查看已连接设备

``` bash
adb devices
```

## 设备连接管理

### USB连接

- 硬件设备正常

- Android开发者模式和USB调试模式已打开

- 设备驱动正常

- USB连接正常

### WLAN连接（需要USB线）

- 设备与电脑在同一wifi下

- 设备与电脑USB连接正常

- 电脑监听`5555`端口

``` bash
adb tcpip 5555
```

- 断开USB连接

- 找到设备IP地址

- 使用IP地址连接设备

``` bash
adb connect <ip_address>
```

### WLAN连接（不需要USB线）

- 设备与电脑在同一wifi下

- 打开设备终端（使用`系统自带终端`或者`Termux`等第三方软件）

- 开放端口

``` bash
su
setprop service.adb.tcp.port 5555
```

- 使用ip地址连接设备

``` bash
adb connect <ip_address>
```

### WLAN连接切换USB连接

``` bash
adb usb
```

### 断开网络连接

``` bash
adb disconnect <ip_address>
```

## 应用管理

### 查看所有应用

> `-s`：系统应用
> `-3`：第三方应用

``` bash
adb shell pm list packages
adb shell pm list packages -s
adb shell pm list packages -3
```

### 模糊查找应用

``` bash
adb shell pm list packages <package_name>
```

### 安装应用

> `-l`：将应用安装到保护目录`/mnt/asec`
> `-r`：允许覆盖安装
> `-s`：将应用安装到SDcard
> `-d`：允许降级覆盖安装
> `-g`：授予所有运行时权限

``` bash
adb install <package_name>.apk
```

### 卸载应用

> `-k`：保留数据

``` bash
adb uninstall <package_name>
```

### 清除应用数据

``` bash
adb shell pm clear <package_name>
```

### 查看正在运行的Services

``` bash
adb shell dumpsys activity services
adb shell dumpsys activity services <package_name>
```

### 查看应用详细信息

``` bash
adb shell dumpsys package <package_name>
```

### 查看应用安装路径

``` bash
adb shell pm path <package_name>
```

### 强制停止应用

``` bash
adb shell am force-stop <package_name>
```

## 文件管理

### 从设备下载电脑

> `<remote>`：设备文件路径
> `<local>`：电脑的目录

``` bash
adb pull <remote>
adb pull <remote> <local>
```

### 从电脑上传到设备

``` bash
adb push <local> <remote>
```

### 查看目录内容

> `-a`：列出所有文件及隐藏文件
> `-i`：列出所有文件及索引编号
> `-s`：列出所有文件及文件大小
> `-n`：列出所有文件及UID、GID
> `-R`：列出所有文件及其目录子文件
> `<directory>`：目录

``` bash
adb shell ls
adb shell ls <directory>
```

### 切换目录

``` bash
adb shell cd <directory>
```

### 删除文件

> `-f`：强制删除
> `-r`：递归操作
> `-d`：对目录的操作
> `-i`：删除前提示

``` bash
adb shell rm <file_name>
```

### 创建目录

> `-m`：赋予读写权限
> `-p`：指定目录及父目录

``` bash
adb shell mkdir <directory_name>
```

### 创建文件

> `-n`：文件的时间

``` bash
adb shell touch <file_name>
```

### 复制文件

> `<source>`：源路径
> `<dest>`：目标路径

``` bash
adb shell cp <source> <dest>
```

### 移动或重命名文件

``` bash
adb shell mv <source> <dest>
```

## 网络管理

### 查看网络统计信息

``` bash
adb shell netstat
```

### 测试网络间的连接和延迟

> `-c <num>`：次数

``` bash
adb shell ping <URL>
```

## 模拟按键/输入

> `<keycode>`：[Android 键码值](https://feiju12138.github.io/2019/12/23/Android键码值/)

``` bash
adb shell input keyevent <keycode>
```

### 滑动解锁

> `<start_x>`：起始位置x坐标
> `<start_y>`：起始位置y坐标
> `<stop_x>`：结束位置x坐标
> `<stop_y>`：结束位置y坐标

``` bash
adb shell input swipe <start_x> <start_y> <stop_x> <stop_y>
```

## 日志打印

### 按级别过滤日志

> `<priority>`：优先级
>> `*:V`：只显示`Verbose`及以上级别（优先级最低）
>> `*:D`：只显示`Debug`及以上级别
>> `*:I`：只显示`Info`及以上级别
>> `*:W`：只显示`Warning`及以上级别
>> `*:E`：只显示`Error`及以上级别
>> `*:F`：只显示`Fatal`及以上级别
>> `*:S`：只显示`Silent`及以上级别（优先级最高）

- `MacOS`下加`""`

``` bash
adb logcat <priority>
adb logcat "<priority>"
```

### 清空已存在的日志

``` bash
adb logcat -c
```

### 将日志显示在控制台

``` bash
adb logcat -d
```

### 将日志输出到文件

``` bash
adb logcat -f <dirctory>
```

### 内核日志

``` bash
adb shell dmesg
```

## 系统属性

### 查看设备系统属性

``` bash
adb shell getprop
```

### 设置设备系统属性

``` bash
adb shell setprop <key> <value>
```

### 查看设备型号

``` bash
adb shell getprop ro.product.model
```

### 查看设备电池状况

``` bash
adb shell dumpsys battery
```

### 查看设备屏幕分辨率

``` bash
adb shell wm size
```

### 查看设备屏幕密度

``` bash
adb shell wm density
```

### 查看设备显示屏参数

``` bash
adb shell dumpsys window displays
```

### 查看设备 android_id

``` bash
adb shell settings get secure android_id
```

### 查看设备IMEI

- `Android 4.4`及以下版本

``` bash
adb shell dumpsys iphonesubinfo
```

- `Android 5.0`及以上版本

``` bash
adb shell
su
service call iphonesubinfo 1
```

### 查看设备 Android 系统版本

``` bash
adb shell getprop ro.build.version.release
```

### 查看设备 IP 地址

``` bash
adb shell ifconfig | grep Mask
adb shell ifconfig wlan0
adb shell netcfg
```

### 查看设备 Mac 地址

``` bash
adb shell cat /sys/class/net/wlan0/address
```

### 查看设备 CPU 信息

``` bash
adb shell cat /proc/cpuinfo
```

### 查看设备内存信息

``` bash
adb shell cat /proc/meminfo
```

### 查看设备更多硬件与系统属性

``` bash
adb shell cat /system/build.prop
```

### 其他

> `<property>`：属性名
>> `ro.build.version.sdk`：SDK 版本
>> `ro.build.version.release`：Android 系统版本
>> `ro.build.version.security_patch`：Android 安全补丁程序级别
>> `ro.product.model`：型号
>> `ro.product.brand`：品牌
>> `ro.product.name`：设备名
>> `ro.product.board`：处理器型号
>> `ro.product.cpu.abilist`：CPU 支持的 abi 列表
>> `persist.sys.isUsbOtgEnabled`：是否支持OTG
>> `dalvik.vm.heapsize`：每个应用程序的内存上限
>> `ro.sf.lcd_density`：屏幕密度

``` bash
adb shell getprop <property>
```

## 刷机命令

### 进入Recovery模式

- 手机重启到卡刷模式

``` sh
adb reboot recovery
```

### 进入Bootloader模式

- 手机重启到线刷模式

``` sh
adb reboot bootloader
```

### 进入9008刷机模式

- 手机重启到9008刷机模式，仅限高通部分机型，慎用

``` sh
adb reboot edl
```

### 等待设备

``` sh
adb wait-for-device
```

## 参考文献

[掘金——往事惘逝](https://juejin.im/post/5b5683bcf265da0f9b4dea96)

