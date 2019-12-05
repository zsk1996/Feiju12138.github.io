---
title: 【笔记】用 HomeBrew 启动关闭服务
date: 2019-12-05 14:57:24
tags:
categories:
- MacOS
---

## 前言

`brew`的隐藏命令，用于管理使用`brew`安装的服务

<!-- more -->

## 基本命令

### 启动服务

``` bash
brew services start <services>
```

### 关闭服务

``` bash
brew services stop <services>
```

### 重启服务

``` bash
brew services restart <services>
```

### 查看已安装服务列表

``` bash
brew services list
```

### 清理已卸载无用的启动配置

``` bash
brew services cleanup
```

## 参考文献

[icyleaf的博客](https://icyleaf.com/2014/01/homebrew-hidden-commands/)

