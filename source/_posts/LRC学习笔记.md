---
title: 【笔记】LRC 学习笔记
date: 2019-12-20 10:24:30
tags:
categories:
---

## 前言

`LRC`是一个可以跟音乐文件做同步的文件格式。当一个音乐文件被电脑音乐播放程序或现代的MP3随身听以及DVD播放机等设备播放时，歌词可以被同步显示出来。（[维基百科](https://zh.wikipedia.org/zh-hans/LRC格式)）

<!-- more -->

## 新建 lrc 文件

``` bash
touch <musicname>.lrc
```

## 基本语法

### 标识标签

> `<musicname>`：歌曲名
> `<artistname>`：艺人名
> `<albumname>`：专辑名
> `<editor>`：LRC作者

> `<compensation>`：时间补偿值，正数为提前，负数为错后
>> 单位：毫秒

``` bash
[ti:<musicname>]
[ar:<artistname>]
[al:<albumname>]
[by:<editor>]
[offset:<compensation>]
```

### 时间标签

> `<mm>`：分钟
> `<ss>`：秒钟
> `<ss>:<xx>`：0.01秒钟
> `<value>`：歌词内容

``` bash
[<mm>:<ss>]<value>
[<mm>:<ss>:<xx>]<value>
```

## 参考文献

[新浪博客——michael_chen](http://blog.sina.com.cn/s/blog_4a34f892010007hg.html)
[KNG的秘密基地的博客](https://kanoha.org/2011/08/14/lrc-extension/)

