---
title: 【笔记】Vim 文件进制转换
categories:
  - MacOS
date: 2020-02-19 16:40:12
---

## 前言

使用`vim`将`2进制文件`和`16进制文件`互相转换

<!-- more -->

## 以2进制的方式打开文件

> `<file>`：需要修改的文件

``` sh
vim -b <file>
```

- 在命令模式下转换进制

### 把文件转换为16进制

``` sh
:%!xxd
```

### 把文件转换为2进制

``` sh
:%!xxd -r
```

### 保存并退出

``` sh
wq
```

## 完成

## 参考文献

[百度知道——npnufn](https://zhidao.baidu.com/question/432259223.html)

