---
title: 【骚操作】Windows10家庭版开启Hyper-V
categories:
  - Windows
date: 2020-07-02 09:04:30
---

## 前言

Microsoft Hyper-V, codenamed Viridian,[1] formerly known as Windows Server Virtualization, is a native hypervisor; it can create virtual machines on x86-64 systems running Windows.[2] Starting with Windows 8, Hyper-V superseded Windows Virtual PC as the hardware virtualization component of the client editions of Windows NT. A server computer running Hyper-V can be configured to expose individual virtual machines to one or more networks. Hyper-V was first released with Windows Server 2008, and has been available without additional charge since Windows Server 2012 and Windows 8. A standalone Windows Hyper-V Server is free, but with command line interface only.（[维基百科](https://en.wikipedia.org/wiki/Hyper-V)）

<!-- more -->

## 制作脚本

- 新建`.cmd`为扩展名的文件

- 编辑内容

``` sh
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt

for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hyper-v.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL

```

## 执行脚本

- 双击运行

## 完成

