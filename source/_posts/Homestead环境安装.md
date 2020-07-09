---
title: 【笔记】Homestead环境安装
categories:
  - MacOS
date: 2020-07-08 20:11:41
---

## 前言

Laravel Homestead is an official, pre-packaged Vagrant box that provides you a wonderful development environment without requiring you to install PHP, a web server, and any other server software on your local machine. No more worrying about messing up your operating system! Vagrant boxes are completely disposable. If something goes wrong, you can destroy and re-create the box in minutes!（[官方文档](https://github.com/laravel/homestead)）

<!-- more -->

## 准备工作

### VirtualBox

- 确保安装最新的VirtualBox

``` sh
brew cask install virtualbox
```

### vagrant

- 确保安装最新的vagrant

``` sh
brew cask install vagrant
```

## 安装

### 下载项目

``` sh
git clone https://github.com/laravel/homestead.git
```

### 进入项目根目录

``` sh
cd homestead
```

### 初始化项目

``` sh
bash init.sh
```

### 配置

``` sh
vim Homestead.yaml
```

### 启动虚拟机

- 首次启动较慢

``` sh
vagrant up
```

### ssh远程连接虚拟机

``` sh
vagrant ssh
```

### 安装laravel开发环境

- 以普通用户身份安装

``` sh
composer create-project laravel/laravel Laravel --prefer-dist
```

## 完成

## 参考文献

[CSDN——东方宏](https://blog.csdn.net/u012274988/article/details/94655364)
[简书——塞外务农](https://www.jianshu.com/p/212bb585eb69)

