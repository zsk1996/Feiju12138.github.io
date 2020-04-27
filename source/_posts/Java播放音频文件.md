---
title: 【笔记】Java 播放音频文件
date: 2019-12-25 12:19:36
tags:
categories:
- Java
---

## 前言

在使用`swing`包做窗口时，播放音频文件

<!-- more -->

## 准备工作

- jlayer.jar

- \<music\>.mp3

## 播放音频文件

### 导入 Jar 包

- 将`jlayer.jar`导入到项目中

- 将`<music.mp3>`复制到项目根目录下的`audio`目录中

`/audio/<music>.mp3`

### 创建文件输入流对象

``` java
File file = new File("./audio/<music>.mp3");
FileInputStream fileInputStream = new FileInputStream(file);
```

### 创建音频播放对象

``` java
Player player = new Player(fileInputStream);
```

### 调用播放方法

``` java
player.play();
```

## 完成

## 参考文献

[百度经验——caoshixuan100](https://jingyan.baidu.com/article/375c8e19063e9f25f2a229d0.html)

