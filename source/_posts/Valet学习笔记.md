---
title: 【笔记】Valet 学习笔记
categories:
  - MacOS
date: 2020-07-18 21:55:28
---

## 前言

Valet 是一个超级快的 Laravel 开发环境。Valet 并不是提到 Vagrant 或者 Homestead，而是提供了一个灵活的、速度极快的替代品，尤其是当你的电脑内存比较小的时候，它将是一个完美的选择。
Valet 只支持 Mac，而且需要你在本地安装 PHP 和 数据库服务，而这些通过 Homebrew 命令可以很容易的实现。Valet 使用极少的资源消耗提供了一个极速的本地开发环境。所以，它非常适合那些只需要 PHP/MySQL 而不需要一个完整的虚拟化开发环境的人。

<!-- more -->

## 准备工作

- 确保80端口没有被占用

- 安装php

``` sh
brew install php
```

## 开始安装

### 安装composer

``` sh
brew install composer
```

### 用composer安装valet

``` sh
composer global require laravel/valet
```

### 踩坑

- 报错：`[dnsmasq] is not installed, installing it now via Brew... `

#### 原因

- 没有安装`dnsmasq`

#### 解决问题

``` sh
brew install dnsmasq
```

### 安装valet

``` sh
valet install
```

## valet命令

### 启动、重启、停止valet

``` sh
valet start
valet restart
valet stop
```

### 安装、卸载valet

``` sh
valet install
valet uninstall
```

### 启动Laravel站点

#### park

- 把当前工作目录作为 Valet 寻找站点的路径

``` sh
mkdir ~/Sites
cd ~/Sites
valet park
```

#### link

把这个目录下所有文件夹都当做独立的不同站点，而当你只需要启动一个站点的时候，可以使用 link 命令

> `<name>`：Laravel项目名称

``` sh
valet link <name>
```

### 分享站点

- 公网访问

``` sh
valet share
```

### 查看日志

``` sh
valet log
```

## 完成

## 参考文献

[Specs的博客](https://9iphp.com/web/laravel/laravel-valet-local-dev-environment.html)
[Vien的博客](https://viencoding.com/article/55)

