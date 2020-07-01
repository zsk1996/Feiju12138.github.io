---
title: 【笔记】Fastboot学习笔记
categories:
  - Android Play Machine
date: 2020-06-28 18:09:08
---

## 前言

快速启动（英语：Fastboot）是一个诊断协议，主要用于由一台计算机通过USB连接Android智能手机，修改其闪存文件系统。它是Android Debug Bridge库的一部分。（[维基百科](https://zh.wikipedia.org/wiki/快速启动)）

<!-- more -->

## 查看已连接设备列表

``` sh
fastboot devices
```

## 获取厂商OEM锁相关信息

``` sh
fastboot oem get_identifier_token
```

## 刷入分区

> `<file>`：刷机包文件位置

### 刷入boot分区

``` sh
fastboot flash boot <file>
```

### 刷入recovery分区

``` sh
fastboot flash recovery <file>
```

### 刷入bootloader

``` sh
fastboot flash bootloader u-boot.bin
```

### 刷入kernel

``` sh
fastboot flash kernel uImage
```

### 刷入system

``` sh
fastboot flash system <file>
```

### 刷入userdata

``` sh
fastboot flash userdata <file>
```

### 刷入ramdisk

``` sh
fastboot flash ramdisk <file>
```

### 一次性刷入分区

> `<zip>`：新建的包含boot.img、system.img、recovery.img的`.zip`压缩包

``` sh
fastboot update <zip>
```

### 刷入开机画面

``` sh
fastboot flash splash1 <file>
```

## 擦除分区

- 擦除boot分区、system分区、userdata分区、cache分区

``` sh
fastboot erase system -w
```

### 擦除boot

``` sh
fastboot erase boot
```

### 擦除system

``` sh
fastboot erase system
```

### 擦除cache

``` sh
fastboot erase cache
```

### 擦除userdata

``` sh
fastboot erase userdata
```

### 擦除nv数据

``` sh
fastboot erase fsg
fastboot erase fsc
fastboot erase modemst1
fastboot erase modemst2
```

## 重启系统

``` sh
fastboot reboot
```

## 不烧写的情况下调试

``` sh
fastboot boot uImage
fastboot boot u-boot.bin
```

## 查看版本号

``` sh
fastboot getver:version
```

## 复位到bootloader

``` sh
fastboot reboot-bootloader
```

## 完成

## 参考文献

[CSDN——蚁人日记](https://blog.csdn.net/nei504293736/article/details/53148575)

