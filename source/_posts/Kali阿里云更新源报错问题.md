---
title: 【踩坑】Kali阿里云更新源报错问题
date: 2019-11-03 19:48:09
tags:
---

## 前言

kali更换了阿里云更新源执行更新命令后报错，错误分别是

- 由于没有公钥，无法验证下列签名：......

- 仓库......没有数字签名，无法安全地用该源进行更新，所以默认禁用该源。

<!-- more -->

![01.png](/images/20191103194809/01.png)

## 解决问题1

- 下载签名

``` bash
wget archive.kali.org/archive-key.asc
```

- 安装签名

``` bash
apt-key add archive-key.asc
```

![02.png](/images/20191103194809/02.png)

## 解决问题2

- 导入签名

``` bash
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 3B4FE6ACC0B21F32
```

![03.png](/images/20191103194809/03.png)

## 完成后更新

- 更新本地软件仓库

![04.png](/images/20191103194809/04.png)

## 参考文献

[CSDN——ayatou666](https://blog.csdn.net/ayatou666/article/details/80092529)

[CSDN——五虎将](https://blog.csdn.net/tankweight/article/details/82948864)
