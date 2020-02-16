---
title: 【笔记】Android逆向 学习笔记
categories:
  - Android
date: 2020-02-14 21:26:03
---

## 前言

`Android逆向工程`学习笔记

<!-- more -->

## APK 文件结构

### assets

- 不经过aapt编译的资源文件

### lib

- 动态链接库，存放`.so`文件

### META-INF

- 文件摘要，摘要加密和签名证书文件目录

#### CERT.RSA

- 公钥和加密算法描述

#### CERT.SF

- 加密文件，它是使用私钥对摘要铭文加密后得到的密文信息，只有使用私钥配对的公钥才能解密该文件

#### MANIFEST.MF

- 程序清单文件，它包含包中所有文件的摘要明文

### res

- 资源文件目录，二进制格式

#### drawable

- 图片资源

#### layout

- 布局资源

#### menu

- 菜单资源

### resources.arsc

- 经过aapt编译过的资源文件

### classes.dex

- 可执行文件

### AndroidManifest.xml

- 配置文件

## APK 打包流程

- 打包资源文件，生成`R.java`和`resources.ap_`文件
- 处理AIDL文件，生成对应的`.java`文件
- 编译Java文件，生成对应的`.class`文件
- 把`.class`文件转化成`Cavik VM`支持的`.dex`文件
- 打包生成未签名的`.apk`文件
- 对未签名的`.apk`文件进行签名
- 对签名后的`.apk`文件进行对齐处理

## APK 安装流程

### 安装方式

#### 系统程序

- 系统程序安装

#### 用户程序

- 安装包手动安装

- 通过应用市场安装

- 通过ADB安装

### 安装过程

- 复制APK安装包到`/data/app`目录下，解压并扫描安装包
- 把`dex`文件保存到`/data/dalvik-cache`目录
- 在`/data/data`目录下创建对应的应用数据目录

### 目录结构

#### /system/app

- 系统自带的应用程序，需要`root`权限才能删除

#### /data/app

- 用户程序安装的目录，安装时把apk文件复制到此目录

#### /data/data

- 存放应用程序的数据

#### /data/dalvik-cache

- 将`apk`中的`dex`安装到`dalvik-cache`目录下

### 卸载过程

- 删除安装过程中在上述三个目录下创建的文件及目录

## APK 反编译与回bianyi

- 先查壳，再反编译看验证
- `.dex`文件转化为`.smali`文件，反编译工具`apktool`
- 去除广告和弹窗，撇开不存在于`smali`的这种情况，容易的就是可以`XML`中找到`Activity`，难得就是找不到，发生这种情况时，就要分析代码，程序逻辑，抓住关键信息、界面和函数

## MacOS 下的反编译

### 准备工作

- Apktool

``` sh
brew install apktool
```

- dex2jar

``` sh
brew install dex2jar
```

- JD-GUI

``` sh
brew cask install jd-gui
```

### 反编译 apk 文件

- 使用`apktool`命令反编译`.apk`文件

> `<name>`：`.apk`文件

``` sh
apktool d <name>
```

### 反编译 dex 文件

- 直接解压缩`.apk`文件

- 使用`d2j-dex2jar`命令，反编译`.dex`文件

``` sh
d2j-dex2jar classes.dex
d2j-dex2jar classes2.dex
```

- 使用`JD-GUI`软件打开`.jar`文件

## 参考文献

[哔哩哔哩——b站最菜黑客](https://www.bilibili.com/video/av81328003)
[简书——CrazyCodeBoy](https://www.jianshu.com/p/48a0f9e6e51a)

