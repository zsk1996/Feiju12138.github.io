---
title: 【笔记】在Mac上搭建Minecraft服务器
categories:
  - Minecraft
date: 2020-03-03 16:01:37
---

## 前言

自己搭一台Minecraft服务器，我的笔记在Mac环境下测试

<!-- more -->

## 准备工作

- 购买正版[Minecraft](https://www.minecraft.net/zh-hans/)

- 服务端jar包[minecraft-server](https://www.minecraft.net/en-us/download/server/)

- 安装Java

## 第一次启动

``` sh
java -Xmx1024M -Xms1024M -jar server.jar
```

### 启动后会报错

``` sh
You need to agree to the EULA in order to run the server. Go to eula.txt for more info.
```

- 此时在当前目录下会生成`eula.txt`文件

### 编辑 eula.txt 文件

``` sh
vim eula.txt
```

### 修改 eula.txt 文件

``` sh
eula=true
```

## 第二次启动（有界面）

``` sh
java -Xmx1024M -Xms1024M -jar server.jar
```

- 启动成功同时会在当前目录生成配置文件

![01.png](/images/20200303160137/01.png)

### 退出

- 在右下角输入`stop`->回车

## 第三次启动（无界面）

- 为了解决非官方版本的好友加入服务器，需要修改配置文件

### 编辑配置文件

``` sh
vim server.properties
```

### 修改配置文件

``` sh
online-mode=false
```

### 启动

``` sh
java -Xmx1024M -Xms1024M -jar server.jar nogui
```

![02.png](/images/20200303160137/02.png)

### 退出

- `ctrl`+`c`

## 踩坑

- 提示：`Outdated server!`

![03.png](/images/20200303160137/03.png)

### 原因

- 服务器版本和游戏版本不相同

### 解决问题

- 下载和游戏相同版本的`minecraft_server`
- 或者下载和服务器版本相同的游戏

## 踩坑

- 提示：`连接终止`

![04.png](/images/20200303160137/04.png)

### 原因

- 可能用了相同的ID

### 解决问题

- 让小伙伴也在官网注册一个ID

## 进入游戏

- 根据ip地址进入服务器，默认端口号为`25565`

- 内网可以使用`127.0.0.1:25565`

- 外网自行配置内网穿透

## 完成

## 参考文献

[MCBBS——guoguo33](https://www.mcbbs.net/thread-839376-1-1.html)
[游戏园——天天](http://minecraft.yxzoo.com/106137)

