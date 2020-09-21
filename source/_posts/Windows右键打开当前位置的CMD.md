---
title: 【笔记】Windows右键打开当前位置的CMD
categories:
  - Windows
date: 2020-09-14 08:08:07
---

## 前言

Windows右键打开当前位置的CMD

<!-- more -->

## 脚本

- 新建`.reg`文件，编辑内容并保存

``` sh
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCMDHere]
"ShowBasedOnVelocityId"=dword:00639bc8

[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCMDHere\command]
@="cmd.exe /s /k pushd \"%V\""
```

- 执行脚本

## 完成

## 参考文献

[ssooking的博客](https://www.cnblogs.com/ssooking/p/8536468.html)

