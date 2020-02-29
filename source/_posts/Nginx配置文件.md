---
title: 【笔记】Nginx配置文件
categories:
  - Server
date: 2020-02-28 18:42:34
---

## 前言

Nginx配置文件学习笔记

<!-- more -->

## 全局块

### worker\_processes

- 这是Nginx服务器并发处理服务的关键配置，`worker_processes`值越大，可以支持的并发处理量也越多，但是会受到硬件、软件等设备的制约

## events 块

- 主要影响Nginx服务器与用户的网络连接

### worker\_connections

- Nginx支持的最大连接数

## http 块

- Nginx服务器配置中最频繁的部分
- http块也可以包括http全局块、server块

### http 全局块

- http全局块配置的指令包括文件引入、MIME-TYPE定义、日志自定义、连接超时时间、单连接请求数上限等

### server 块

- 每个http块可以包含多个server块
- 每个server块就相当于一个虚拟主机

#### 全局 server 块

- 最常见的配置是本虚拟主机的监听配置和本虚拟主机的名称或IP配置

#### location 块

- 一个server块可以配置多个location块
- location块主要作用是基于Nginx服务器接收到的请求字符串，对虚拟主机名称之外的字符串进行匹配，对特定的请求进行处理。地址定向、数据缓存和应答控制等功能，还有许多第三方模块的配置也在这里进行

##### 正则表达式

###### =

- 用于不含正则表达式的URI前，要求请求字符串与URI严格匹配，如果匹配成功，就停止继续向下搜索并立即处理该请求

###### ~

- 用于表示URI包含正则表达式，并且区分大小写

###### ~\*

- 用于表示URI包含正则表达式，并且不区分大小写

###### ^~

- 用于不含正则表达式的URI前，要求Nginx服务器找到标识URI和请求字符串匹配度最高的location后，立即使用此location处理请求，而不再使用location块中的正则URI和请求字符串做匹配

## 参考文献

[哔哩哔哩——尚硅谷官方](https://www.bilibili.com/video/av68136734)

