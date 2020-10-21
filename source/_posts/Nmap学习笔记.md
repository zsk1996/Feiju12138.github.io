---
title: 【笔记】Nmap 学习笔记
date: 2019-12-04 00:08:47
tags:
categories:
- Penetration Tests
---

## 前言

Nmap（网络映射器）是一款用于网络发现和安全审计的网络安全工具，它是自由软件。软件名字Nmap是Network Mapper的简称。（[维基百科](https://zh.wikipedia.org/wiki/Nmap)）

<font color="red">本文仅用于网络信息防御学习</font>

<!-- more -->

## 基本命令

### 普通扫描

``` bash
nmap 192.168.1.1
```

### TCP SYN 扫描

``` bash
nmap -sS 192.168.1.1
```

### 指定端口号扫描

``` bash
nmap -p 8000-8888 192.168.1.1
```

### 显示扫描过程

``` bash
nmap -v 192.168.1.1
```

### 全面的系统扫描

``` bash
nmap -A 192.168.1.1
```

### 使用脚本扫描

``` bash
nmap --script=vuln 192.168.1.1
```

### 系统检测

``` bash
nmap -T4 -O 192.168.1.1
```

## 参考文献

[哔哩哔哩——窝草丶五弦都能断](https://www.bilibili.com/video/av22757067?from=search&seid=13943888877523056337)
[哔哩哔哩——腾讯掌控安全学院](https://www.bilibili.com/video/av58853797?t=3572&spm_id_from=333.337.b_62696c692d6865616465722d6d.25)

