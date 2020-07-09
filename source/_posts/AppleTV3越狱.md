---
title: 【笔记】Apple TV 3 越狱
categories:
  - Apple
date: 2020-07-09 15:06:22
---

## 前言

DNS Apple TV 3 越狱方法

<!-- more -->

## 越狱

- `设置`->`iTunes Store`->`位置`->`United States`

- `设置`->`通用`->`网络`->`Wi-Fi`->选择wifi->`配置DNS`改成手动：46.166.144.59

- `设置`->`通用`->`将数据发送给Apple`（点play键）->`添加描述文件`：http://trailers.apple.com/trailers.cer

- 打开主页的`预告片`->`#etason`->等待自动越狱后重启

- `设置`->`通用`->`网络`->`Wi-Fi`->选择wifi->`配置DNS`改成自动，并记下ip地址

- 用电脑ssh远程连接

> `<ip>`：刚刚记下的ip地址

``` sh
ssh root@<ip>
```

- 密码为：`alpine`

``` sh
dpkg -i /var/root/untether.deb
```

## 移动应用程序文件夹至用户分区（可选）

- 因为系统分区的储存空间不够，需要将应用程序文件夹移动至用户分区。

``` sh
mkdir -p /private/var/Applications
cd /Applications
mv * /private/var/Applications
cd /
rmdir /Applications
ln -s /private/var/Applications /Applications
```

## 安装Kodi 14.2（可选）

``` sh
wget -O- http://apt.awkwardtv.org/awkwardtv.pub | apt-key add -
echo "deb http://apt.awkwardtv.org/ stable main" > /etc/apt/sources.list.d/awkwardtv.list
echo "deb http://mirrors.kodi.tv/apt/atv2 ./" > /etc/apt/sources.list.d/xbmc.list
apt-get update
apt-get install org.xbmc.kodi-atv2
```

## 安装nitoTV（可选）

``` sh
echo "deb http://apt.awkwardtv.org/ stable main" > /etc/apt/sources.list.d/awkwardtv.list
apt-get update
apt-get install com.nito.nitoTV
```

## 完成

## 参考文献

[YANG的博客](https://syy.hk/archives/2091.html)
[KubaDownload的博客](https://kubadownload.com/news/jailbreak-apple-tv-3/)

