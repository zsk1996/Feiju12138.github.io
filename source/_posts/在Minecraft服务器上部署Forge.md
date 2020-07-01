---
title: 【笔记】在Minecraft服务器上部署Forge
categories:
  - Minecraft
date: 2020-06-24 09:12:20
---

## 前言

在Minecraft服务器上部署Forge，使服务器也可以安装Mod

<!-- more -->

## 准备工作

- 对应版本的[Forge](http://files.minecraftforge.net)

## 客户端安装Forge

- 在`Minecraft Launcher`->`配置`->添加对应版本的游戏

- 运行Forge安装程序（默认选择`Install client`）

``` sh
java -jar forge-1.15.2-31.2.22.jar
```

## 下载服务器Forge

- 在新建一个目录

``` sh
mkdir mincraft-server
```

- 运行Forge安装程序，选择`Install server`，位置选择刚刚新建的目录

``` sh
java -jar forge-1.15.2-31.2.22.jar
```

## 打包并发送到云端

- 打包下载好的包含Froge的服务器软件

``` sh
tar -cvf minecraft-server.tar minecraft-server/
```

- 发送到云端

``` sh
scp minecraft-server.tar root@39.104.62.91:/root
```

## 云端解压并安装

- 解压

``` sh
tar -xvf minecraft-server.tar
```

- 第一次启动

``` sh
cd minecraft-server
java -Xmx1024M -Xms1024M -jar forge-1.15.2-31.2.22.jar nogui
```

- 同意授权

``` sh
vim eula.txt
```

- 修改`false`为`true`

- 第二次启动

``` sh
java -Xmx1024M -Xms1024M -jar forge-1.15.2-31.2.22.jar nogui
```

## 完成

- 注意，客户端和服务器端要保持相同版本的游戏及Forge，要同时安装相同的Mod

## 参考文献

[YouToBe——thebluecrusader](https://www.youtube.com/watch?v=AEU4efZuPeI)

