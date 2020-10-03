---
title: 【笔记】将iOS备份移到外置磁盘
categories:
  - Apple
date: 2020-07-21 18:37:05
---

## 前言

将iOS备份移到外置磁盘，节省Mac硬盘的占用

<!-- more -->

## 保留旧备份（可选）

- 进入到iOS备份的目录

``` sh
open ~/Library/Application Support/MobileSync/
```

- 将`Backup`更名为`Backup.default`

## 开始转移

- 复制`~/Library/Application Support/MobileSync/`下的`Backup`目录到外置磁盘根目录

- 建立软连接

> `<name>`：外置磁盘的目录名

``` sh
ln -s /Volumes/<name>/Backup ~/Library/Application\ Support/MobileSync/Backup
```

## 完成

## 参考文献

[少数派](https://sspai.com/post/33524)

