---
title: 【笔记】IDEA在创建Maven项目后添加依赖
categories:
  - Java
date: 2020-09-29 10:04:56
---

## 前言

IDEA在创建Maven项目后，使用插件，实现自动添加依赖

<!-- more -->

## 添加依赖

- `Intellij IDEA`->`Preferences`->`Plugins`->`Marketplace`->搜索`EditStarters`->`Install`

![01.png](/images/20200929100456/01.png)

- 打开项目`pom.xml`文件->将光标移到`<dependencies></denpendencies>`标签内->MacOS使用快捷键`ctrl`+`return`（或`command`+`n`），Windows使用`alt`+`insert`->`Edit Starters`

![02.png](/images/20200929100456/02.png)

- 修改starter源->`OK`

![03.png](/images/20200929100456/03.png)

- 双击进行添加依赖或移除依赖

## 完成

## 参考文献

[CSDN——许洛以合](https://blog.csdn.net/w1043203101/article/details/79688848)
[CSDN——山鬼谣弋痕夕](https://blog.csdn.net/weixin_30363263/article/details/84380805)

