---
title: 【笔记】MacOS制作图标文件
date: 2019-12-07 08:53:57
tags:
categories:
- MacOS
---

## 前言

MacOS制作图标文件

<!-- more -->

## 准备工作

- `.png`格式文件

## 安装icoutils

``` sh
brew install icoutils
```

## 准备各尺寸图标

- 创建一个临时目录存放不同大小的图片

``` bash
mkdir tmp.iconset
```

- 把原图片转为不同大小的图片，并放入上面的临时目录

> `<name>`：图片文件名

``` bash
sips -z 16 16 <name>.png --out tmp.iconset/icon_16x16.png
sips -z 32 32 <name>.png --out tmp.iconset/icon_16x16@2x.png
sips -z 32 32 <name>.png --out tmp.iconset/icon_32x32.png
sips -z 64 64 <name>.png --out tmp.iconset/icon_32x32@2x.png
sips -z 128 128 <name>.png --out tmp.iconset/icon_128x128.png
sips -z 256 256 <name>.png --out tmp.iconset/icon_128x128@2x.png
sips -z 256 256 <name>.png --out tmp.iconset/icon_256x256.png
sips -z 512 512 <name>.png --out tmp.iconset/icon_256x256@2x.png
sips -z 512 512 <name>.png --out tmp.iconset/icon_512x512.png
sips -z 1024 1024 <name>.png --out tmp.iconset/icon_512x512@2x.png
```

## 转换为icns格式

- 使用`iconutil`工具将`tmp.iconset`目录转换为`.icns`图标文件

> `<name_new>`：转换后的图标文件名

``` bash
iconutil -c icns tmp.iconset -o <name_new>.icns
```

## 转换为ico格式

- 使用`icotool`工具将`tmp.iconset`目录内的所有图片转换为`.icns`图标文件

``` bash
cd tmp.iconset
icotool -c insong_16x16.png insong_32x32.png insong_64x64.png insong_128x128.png insong_256x256.png insong_512x512.png -o <name_new>.ico
```

## 完成

