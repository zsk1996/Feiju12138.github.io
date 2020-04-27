---
title: 【骚操作】QQ微信消息轰炸
date: 2019-12-06 20:39:22
tags:
---

## 前言

用`.vbs`脚本实现QQ微信消息轰炸

<!-- more -->

## 编写脚本

- 新建文本文件->重命名->"QQ微信消息轰炸.vbs"->确认修改扩展名

- 右键->编辑->输入代码->保存

> `<昵称>`轰炸对象的昵称
> `<次数>`轰炸执行次数
> `<间隔>`每次轰炸间隔（毫秒）

``` bash
Set WshShell= WScript.CreateObject("WScript.shell")
wshShell.AppActivate"<网名>"
for i=1 to <次数>
WScript.sleep <间隔>
WshShell.SendKeys "^v"
WshShell.SendKeys "%s"
Next
```

## 运行脚本

- 在消息编辑文本框内输入想要轰炸的内容

- 选中->右键->剪切

- 直接双击运行程序

## 完成

![01.gif](/images/20191206203922/01.gif)

