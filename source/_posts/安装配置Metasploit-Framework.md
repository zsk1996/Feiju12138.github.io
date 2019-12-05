---
title: 【笔记】安装配置 Metasploit Framework
date: 2019-11-16 16:30:21
tags:
categories:
- 网络安全
---

## 前言

Metasploit项目是一个旨在提供安全漏洞信息计算机安全项目，可以协助安全工程师进行渗透测试（penetration testing）及入侵检测系统签名开发。[维基百科](https://wikipedia.hk.wjbk.site/zh-cn/Metasploit)

<!-- more -->

## 下载安装 Metasploit Framework

- 其他系统可以在 [Metasploit Framework 官网](https://www.metasploit.com) 下载

- 我使用的MacOS，安装方式是HomeBrew

- 在终端使用brew安装并自动编译Metasploit

``` bash
brew search Metasploit
brew cask install metasploit
```

- 安装编译完成

![01.png](/images/20191116163021/01.png)

## 配置

### 首次启动

- 安装编译完成后，首次启动Metasploit将开始配置引导

- 进入软件根目录

``` bash
cd /opt/metasploit-framework/bin/
```

- 启动Metasploit

``` bash
./msfconsole
```

### 配置引导

- 您是否要使用和设置新数据库（推荐）？

> Would you like to use and setup a new database (recommended)? yes

- MSF Web服务帐户的初始用户名？

> Initial MSF web service account username? : root

- MSF Web服务帐户的初始密码？ （留空为随机密码）

> Initial MSF web service account password? (Leave blank for random password): 123456

## 完成

- 配置完成后，首次启动

![02.png](/images/20191116163021/02.png)

## 参考文献

[驱蚊器喵#ΦωΦ](https://blog.meow.page/2019/04/07/metasploit-on-mac/)
