---
title: 【笔记】Charles 学习笔记
categories:
  - MacOS
date: 2020-04-07 07:52:05
---

## 前言

Charles是MacOS上最常用的抓包工具

<!-- more -->

## 准备工作

- Charles.app

## 配置

### 配置端口号

- `Proxy`->`Proxy Settings`

![01.png](/images/20200407075205/01.png)

- 默认端口号为`8888`

- 勾选`Enable transparent HTTP proxying`

![02.png](/images/20200407075205/02.png)

## 认证证书

- `Help`->`SSL Proxying`->`Save Charles Root Certificate`

- 将证书保存到本地，在需要认证的设备上打开`charles-ssl-proxying-certificate.pem`文件

![03.png](/images/20200407075205/03.png)

## 配置代理

- 不同设备的代理配置方法详见另一篇博文

> `ip`：电脑的ip地址
> `端口号`：8888

[传送门](/2019/12/28/Lantern代理共享给整个局域网)

## 踩坑

### 左下角报错：Denying access from address not on ACL

- `Proxy`->`Access Control Settings`

![04.png](/images/20200407075205/04.png)

- 将需要被抓包的设备的ip地址配置到`Access Control Settings`即可

![05.png](/images/20200407075205/05.png)

### vivo手机安装证书

- 将文件扩展名`.pem`改为`.crt`

## 完成

## 参考文献

[知乎——Zkerhcy](https://zhuanlan.zhihu.com/p/26182135)
[简书——从心开始的我](https://www.jianshu.com/p/8385a13b0e5c)
[浅鱼的博客](https://www.runtofuture.cn/index.php/archives/698/)

