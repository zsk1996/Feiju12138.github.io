---
title: 【踩坑】关闭Mac开机自启Apache
categories:
  - MacOS
date: 2020-02-28 19:43:35
---

## 前言

设置Mac自带的Apache开机自启

<!-- more -->

## 关闭

``` sh
sudo launchctl unload -w /System/Library/LaunchDaemons/org.apache.httpd.plist
```

## 开启

``` sh
sudo launchctl load -w /System/Library/LaunchDaemons/org.apache.httpd.plist
```

## 参考文献

[简书——haokeed](https://www.jianshu.com/p/b015b6375cf4)

