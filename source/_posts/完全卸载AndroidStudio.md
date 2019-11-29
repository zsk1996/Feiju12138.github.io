---
title: 【笔记】完全卸载 Android Studio
date: 2019-11-28 17:13:17
tags:
---

## 前言

`Android Studio`在使用过后，由于会下载很多Android相关工具的资源包，所以直接移到废纸篓的方式无法卸载干净，通过命令行，可以完全卸载

<!-- more -->

## 完全卸载

### 卸载Android Studio应用及相关配置

``` bash
rm -Rf /Applications/Android\ Studio.app
rm -Rf ~/Library/Preferences/AndroidStudio*
rm ~/Library/Preferences/com.google.android.studio.plist
rm -Rf ~/Library/Application\ Support/AndroidStudio*
rm -Rf ~/Library/Logs/AndroidStudio*
rm -Rf ~/Library/Caches/AndroidStudio*
```

### 删除项目文件

``` bash
rm -Rf ~/AndroidStudioProjects
```

### 删除依赖文件

``` bash
rm -Rf ~/.gradle
```

### 删除AVD缓存

``` bash
rm -Rf ~/.android
```

### 删除Android SDK Tools文件

``` bash
rm -Rf ~/Library/Android*
```

## 完成

## 参考文献

[CSDN——huangjie_android](https://blog.csdn.net/huagjie/article/details/79691078)

