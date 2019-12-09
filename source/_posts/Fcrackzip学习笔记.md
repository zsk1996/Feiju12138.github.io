---
title: 【笔记】Fcrackzip 学习笔记
date: 2019-12-05 16:06:17
tags:
categories:
- 网络安全
---

## 前言

fcrackzip是一款专门破解zip类型压缩文件密码的工具，工具小巧方便、破解速度快，能使用字典和指定字符集破解，适用于Linux、MacOS系统

<!-- more -->

## 基本命令

### 指定字符集破解.zip

> `a`表示小写字母
> `A`表示大写字母
> `l`表示阿拉伯数字
> `!`表示特殊字符
> `:`表示包含冒号之后的字符

``` bash
fcrackzip -c 'aAl' <filename>
```

### 使用暴力破解

``` bash
frackzip -b <filename>
```

### 密码长度

``` bash
frackzip -l 1-10 <filename>
```

### 只显示破解成功的密码

``` bash
frackzip -u <filename>
```

### 使用字典破解

``` bash
frackzip -D -p <dictionary> <filename> 
```

## 参考文献

[Lybbn——laoyan](http://www.lybbn.cn/data/datas.php?yw=133)

