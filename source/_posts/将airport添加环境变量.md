---
title: 【笔记】将 airport 添加环境变量
categories:
  - MacOS
date: 2020-01-14 01:59:49
---

## 前言

在`MacOS`命令行下，将`airport`添加环境变量

<!-- more -->

## 基本命令

``` sh
sudo ln -s /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport /usr/local/bin/airport
```

## 完成

