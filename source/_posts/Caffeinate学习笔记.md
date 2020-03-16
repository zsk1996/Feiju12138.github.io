---
title: 【笔记】Caffeinate 学习笔记
categories:
  - MacOS
date: 2020-03-15 20:58:57
---

## 前言

使用caffeinate命令使系统停止休眠

<!-- more -->

## 基本命令

- 使系统停止休眠，停止程序需`control`+`c`手动退出

``` sh
caffeinate
```

### 设定倒计时

- 倒计时结束后结束程序

> `<time>`：单位：秒

``` sh
caffeinate -t <time>
```

### 定位应用

- 将程序与其他应用定位，当应用运行时，停止屏幕休眠

> `<app>`：被定位应用的路径

``` sh
caffeinate <app>
```

### 其他参数

> `-d`：将阻止显示器进入睡眠状态
> `-i`：将防止系统空闲睡眠
> `-m`：将阻止磁盘进入睡眠
> `-s`：将阻止机器在插入时进入睡眠状态
> `-u`：复制当前活动的用户

## 参考文献

[mos86](https://mos86.com/1113.html)

