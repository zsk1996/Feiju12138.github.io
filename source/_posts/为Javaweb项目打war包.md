---
title: 【笔记】为Javaweb项目打war包
categories:
  - Java
date: 2020-08-05 18:17:09
---

## 前言

为Javaweb项目打war包

<!-- more -->

## 打war包的优点

- 可以压缩为单个文件，节省空间，提升传输效率
- 当`.war`包存放到tomcat服务器的`webapps`目录下，此时启动tomcat服务器会自动解压部署

## 操作方法

- 全选项目根目录的所有子文件和子目录
- 对选中的所有文件压缩为`.zip`格式压缩包
- 将扩展名修改为`.war`

## war包自动部署失败原因

- 在将web项目压缩时，没有采用`.zip`的格式，而是其他格式例如`.rar`
- 打成war包的名字和服务器中已发布的web应用重名
- war包中包含中文文件名或中文目录名

## 参考文献

[哔哩哔哩——江小黑888](https://www.bilibili.com/video/BV1Hg4y1B7dr?p=2)

