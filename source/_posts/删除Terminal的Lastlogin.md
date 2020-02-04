---
title: 【踩坑】删除 Terminal 的 Last login
categories:
  - MacOS
date: 2020-01-31 02:46:56
---

## 前言

删除`MacOS`下`Terminal`的上次终端启动时间显示

<!-- more -->

![01.png](/images/20200131014656/01.png)

## 问题解决

``` sh
touch ~/.hushlogin
```

## 完成

- 重启`Terminal`

![02.png](/images/20200131014656/02.png)

## 参考文献

[码农俱乐部——fharum](https://mlog.club/article/3885147)

