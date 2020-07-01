---
title: 【笔记】Poweroff学习笔记
categories:
  - Linux
date: 2020-06-16 18:00:06
---

## 前言

Poweroff学习笔记

<!-- more -->

## 命令

> `<option>`选项

> `-n`：关闭操作系统时不执行sync操作；
> `-w`：不真正关闭操作系统，仅在日志文件“/var/log/wtmp”中；
> `-d`：关闭操作系统时，不将操作写入日志文件“/var/log/wtmp”中添加相应的记录；
> `-f`：强制关闭操作系统；
> `-i`：关闭操作系统之前关闭所有的网络接口；
> `-h`：关闭操作系统之前将系统中所有的硬件设置为备用模式。

``` sh
poweroff <option>
```

### 立即关闭系统

``` sh
poweroff
```

## 完成

## 参考文献

[Linux命令大全](https://man.linuxde.net/poweroff)

