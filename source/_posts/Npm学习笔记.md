---
title: 【笔记】Npm学习笔记
categories:
  - HTML/CSS/JS
date: 2020-09-23 20:57:41
---

## 前言

npm（全称 Node Package Manager，即“node包管理器”）是Node.js默认的、用JavaScript编写的软件包管理系统。（[维基百科](https://zh.wikipedia.org/wiki/Npm)）

<!-- more -->

## 安装Npm

- 安装Nodejs默认会预装Npm

``` sh
brew install node
```

## 模块位置

### 本地位置

- 在终端当前目录下会产生`node_modules`目录

### 全局位置

- MacOS会在`/usr/local/lib/`目录下产生`node_modules`目录

## 安装模块

> `<package>`：软件包名

``` sh
npm install <package>
```

### 全局操作

> `-g`：全局操作

``` sh
npm install <package> -g
```

#### 升级自身

``` sh
npm install npm -g
```

## 卸载模块

``` sh
npm uninstall <package>
```

## 查看已安装模块

``` sh
npm ls
npm list
```

### 查看指定已安装模块

``` sh
npm list <package>
```

## 查找模块

``` sh
npm search <package>
```

## 升级模块

``` sh
npm update <package>
```

## 清空本地缓存

``` sh
npm cache clear
```

## 查看帮助

``` sh
npm help
```

### 查看指定命令帮助

> `<command>`：命令名

``` sh
npm help <command>
```

## 使用淘宝镜像

- 国内使用淘宝镜像实现加速效果

``` sh
npm install -g cnpm

npm install -g cnpm --registry=https://registry.npm.taobao.org
```

### 国内版Npm命令

``` sh
cnpm install <package>
```

## 完成

## 参考文献

[菜鸟笔记](https://www.runoob.com/nodejs/nodejs-npm.html)
[CSDN——idomyway](https://blog.csdn.net/idomyway/article/details/85226579)
