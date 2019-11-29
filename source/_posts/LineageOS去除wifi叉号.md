---
title: 【踩坑】LineageOS 去除wifi叉号
date: 2019-11-23 23:53:04
tags:
---

## 前言

安装完 LineageOS 系统后，连接wifi显示红叉，事实上有网络，只不过互联网检测默认访问的是谷歌自家的验证服务器，然而谷歌被"墙"了，所以导致没办法评估网络，显示感叹号或叉号

<!-- more -->

## 准备工作

- adb工具

## 去除叉号

- 手机连接电脑

- 使用`adb工具`查看是否正常连接手机

``` bash
adb devices
```

- 进入安卓的shell模式

``` bash
adb shell
```

- 通过修改设置去除叉号

``` bash
delete global captive_portal_http_url
delete global captive_portal_https_url
put global captive_portal_http_url http://developers.google.cn/generate_204
put global captive_portal_https_url https://developers.google.cn/generate_204
```

## 完成

## 参考文献

[QQ群——世界隐性-资源及讨论](https://jq.qq.com/?_wv=1027&k=5lGp1Yv)

