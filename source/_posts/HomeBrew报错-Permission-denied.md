---
title: 【踩坑】HomeBrew报错："Permission denied @ ..."
date: 2019-12-03 23:13:28
tags:
categories:
- MacOS
---

## 前言

`HomeBrew`更新后，每一次执行完`brew upgrade`命令后，`brew`都会自动执行`brew cleanup`命令，但是由于权限问题会报错："Permission denied @ ..."

<!-- more -->

## 解决

- 首先想到的办法是手动删除`brew cleanup`命令提示删除而有删不掉的有权限的文件

然而结局是，删除一个还会有其他的垃圾文件需要清理，没有从根本解决问题

- `stackoverflow`查到一种解决办法，降低`/usr/local/`目录的访问权限

``` bash
sudo chown -R "$(whoami)":admin /usr/local
```

结局是高版本MacOS系统不允许这样操作，提示错误："chown: /usr/local: Operation not permitted"

- `范永勇的博客`查到一种解决办法，提高`brew`访问权限

``` bash
sudo chown -R $(whoami) $(brew --prefix)/*
```

## 成功

![01.png](/images/20191203231328/01.png)

## 参考文献

[stackoverflow——SoftTimur](https://stackoverflow.com/questions/54682876/brew-cleanup-error-permission-denied-unlink-internal)
[范永勇的博客](http://www.fanyeong.com/2017/12/14/homebrew-update-fail/)

