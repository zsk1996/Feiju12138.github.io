---
title: 【笔记】Termux 安装 Arch Linux
categories:
  - 刷机
date: 2020-02-11 00:10:37
---

## 前言

This Termux bash setup shell script will attempt to set Arch Linux up in your Termux environment.（[GitHub](https://github.com/sdrausty/TermuxArch)）

<!-- more -->

## 准备工作

- Termux.app

## 安装依赖包

``` sh
pkg install bsdtar
```

## 克隆项目

### 安装 git

``` sh
pkg install git
```

### 克隆项目到本地

``` sh
git clone https://github.com/sdrausty/TermuxArch
```

### 安装 Arch Linux

- 运行安装脚本自动安装

``` sh
cd TermuxArch
./setupTermuxArch.sh
```

### 安装完成

![01.png](/images/20200211001037/01.png)

- 首次安装完成自动启动

## 启动 Arch Linux

``` sh
startarch
```

## 完成

## 参考文献

[GitHub——SDRausty](https://github.com/termux/termux-app/issues/397)

