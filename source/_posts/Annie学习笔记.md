---
title: 【骚操作】Annie 学习笔记
date: 2019-12-26 13:11:46
tags:
---

## 前言

`Annie`是使用Go构建的快速，简单，干净的视频下载器。（[官网](https://github.com/iawia002/annie)）

<!-- more -->

## 安装

``` bash
brew install annie
```

## 所需依赖

- FFmpeg

## 下载视频

### 直接下载

``` bash
annie <url>
annie <url_1> <url_2>
```

### 查看详情

``` bash
annie -i <url>
```

### 下载列表

#### 下载整个列表

``` bash
annie -p <url>
```

#### 下载选定列表

> `-start`：指定开始小节
> `-end`：指定结束小节
> `-items`：列出想要下载的小节

``` bash
annie -start <num> -end <num> <url>
annie -items <num_1>,<num_2> <url>
```

### 网络代理

#### HTTP 代理

``` bash
annie -x <http_proxy> <url>
```

#### SOCKS5 代理

``` bash
annie -s <socks5_proxy> <url>
```

### 多线程

``` bash
annie -n <num> <url>
```

### 恢复下载

- 重复执行上一次操作

### 短链接下载

> `<av_num>`：`bilibili`中的`av`编号
> `<ep_num>`：`bilibili`中的`ep`编号

``` bash
annie av<av_num>
annie ep<ep_num>
```

### 指定文件存放路径及名称

``` bash
annie -o <directory>
annie -O <filename>
```

## 完成

