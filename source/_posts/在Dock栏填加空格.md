---
title: 【笔记】在Dock栏填加空格
categories:
  - MacOS
date: 2020-04-16 18:19:15
---

## 前言

在MacOS下的Dock栏填加空格，用于分割图标

<!-- more -->

## 添加分隔符

- 打开终端

### 在左半部分添加空格

``` sh
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'
```

### 在右半部分添加空格

``` sh
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}';killall Dock
```

### 重启Dock栏

- 每次添加完，都要重启Dock栏才会刷新出空格

``` sh
killall Dock
```

## 删除分隔符

- 将空格拖拽到外面，就可以清除空格

## 完成

## 参考文献

[知乎——隔壁cookie](https://www.jianshu.com/p/d94f7a214f9e?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)

