---
title: 【笔记】Lantern 代理共享给整个局域网
categories:
  - MacOS
date: 2019-12-28 22:56:15
---

## 前言

蓝灯是一款用于突破网络审查的开源代理软件。 蓝灯的CEO和首席开发者亚当·菲斯克是LimeWire和LittleShoot的前首席工程师。（[维基百科](https://zh.wikipedia.org/wiki/蓝灯)）

<!-- more -->

## 准备工作

- 可以正常使用的`Lantern.app`

## 操作方法

### 修改默认

- 打开终端

- 修改`Lantern`的默认代理IP

``` shell
/Applications/Lantern.app/Contents/MacOS/lantern -addr 0.0.0.0:52909
```

### 连接方法

- 首先查看本机局域网IP地址

``` shell
ifconfig
```

- 根据局域网IP手动配置代理

> `<ip_address>`：本机局域网IP地址
> `52909`：端口号

#### MacOS 连接方法

- `系统偏好设置`->`网络`->`高级`->`代理`

- 分别将`网页代理`、`安全网页代理`手动修改`ip地址`和`端口号`

![01.png](/images/20191228225615/01.png)

- `好`->`应用`

#### IOS 配置方法

- `设置`->`无线局域网`

- 进入wifi配置

- 在`HTTP代理`中进入`代理配置`

- `手动`->手动修改`ip地址`和`端口号`

![02.png](/images/20191228225615/02.png)

- `存储`

#### Android 配置方法

- `设置`->`网络和互联网`->`WLAN`

- 选择要连接的wifi并在连接时选择`高级选项`

- 在`代理`设置选择`手动`

- 手动修改`ip地址`和`端口号`

- `保存`

![03.png](/images/20191228225615/03.png)

### 还原默认

- 将`Lantern`代理IP修改为默认值

``` shell
/Applications/Lantern.app/Contents/MacOS/lantern -addr 127.0.0.1:52909
```

## 参考文献

[简书——Yao_Fairytale](https://www.jianshu.com/p/2ca22bbc3809)

