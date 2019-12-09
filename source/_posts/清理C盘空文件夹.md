---
title: 【骚操作】清理C盘空文件夹
date: 2019-12-07 09:41:43
tags:
categories:
- Windows
---

## 前言

批处理清理C盘空文件夹

<!-- more -->

## 清理空文件夹

- 创建一个`.bat`批处理文件

- 右键->编辑->写入代码->保存

``` bash
@echo off
for %%i in (c) do (
	if exist %%i:\(
		for /f "delims=" %%a in ('dir /ad /b /s "%%i:\"^|sort /r') do (
			rd "%%a">nul 2>nul &&echo 空目录"%%a"删除成功！
		)
	)
)
pause
```

- 右键->运行

## 完成

