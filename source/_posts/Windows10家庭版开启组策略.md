---
title: 【骚操作】Windows10家庭版中开启组策略编辑器
date: 2019-11-02 16:56:14
tags:
categories:
- Windows
---

## 前言

经常有一些小伙伴，在使用Windows10家庭版的时候，需要打开组策略编辑器进行一些高端操作，然而不尽人意，Windows10家庭版默认没有开启此功能，通常会出现"Windows找不到'gpedit.msc'。请确定文件名是否正确后，再试一次。"的警告，今天我就教大家如何在Windows10家庭版中开启组策略编辑器

<!-- more -->

![01.png](/images/20191102165614/01.png)

## 创建文件

- 在任意文件夹中空白处，右键->新建->文本文档

![02.png](/images/20191102165614/02.png)

## 修改文件扩展名

- 右键->重命名->"垃圾清理.bat"->(是否更改扩展名)是

![03.png](/images/20191102165614/03.png)

## 写入代码

- 右键->编辑->写入代码->保存->关闭

![04.png](/images/20191102165614/04.png)

``` bash
@echo off

pushd "%~dp0"

dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt

dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt

for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"C:\Windows\servicing\Packages\%%i"

pause
```

## 运行程序

- 右键->以管理员方式运行

![05.png](/images/20191102165614/05.png)

## 完成

![06.png](/images/20191102165614/06.png)

## 打开"组策略编辑器"

- 开始菜单->Windows系统->运行

![07.png](/images/20191102165614/07.png)

- 输入"gpedit.msc"

![08.png](/images/20191102165614/08.png)

- 打开"本地组策略编辑器"

![09.png](/images/20191102165614/09.png)

## 参考文献

百度
