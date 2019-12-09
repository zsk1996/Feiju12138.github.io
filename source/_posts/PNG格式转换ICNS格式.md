---
title: 【笔记】PNG格式 转换 ICNS格式
date: 2019-12-07 08:53:57
tags:
categories:
- MacOS
---

## 前言

在MacOS上更换软件图标和Windows上有所不同，第一件事就是制作一个`.icns`格式的图标文件

<!-- more -->

## 准备工作

- 1024\*1024的`<name>.png`图片

## 制作图标文件

- 创建一个临时目录存放不同大小的图片

``` bash
mkdir tmp.iconset
```

- 把原图片转为不同大小的图片，并放入上面的临时目录

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

- 使用`iconutil`工具将`tmp.iconset`目录转换为`Icon.icns`图标文件

``` bash
iconutil -c icns tmp.iconset -o Icon.icns
```

## 完成

