---
title: 【笔记】通过XSS拿到网站cookie
categories:
  - Penetration Tests
date: 2020-03-27 18:10:13
---

## 前言

通过XSS拿到网站cookie实现无密码登录

<font color="red">本文仅用于网络信息防御学习</font>

<!-- more -->

## 准备工作

- [XSSPT平台](https://xss.pt/xss.php)

## 在XSSPT平台创建项目

- 我的项目->创建

- 在创建项目中编辑`项目名称`和`项目描述`->下一步

- 勾选`默认模块`->勾选`keepsession`->下一步

## 植入代码

- 将XSSPS平台提供的代码植入到具有XSS漏洞的网站

![01.png](/images/20200327181013/01.png)

- 等待管理员上钩

## 获取cookie

![02.png](/images/20200327181013/02.png)

## 使用cookie

- 打开浏览器开发者模式->选择`Application`->选择`Cookies`中需要渗透的网址->双击空白处添加新的Cookie

> `Name`：获取的cookie`=`左面的内容
> `Value`：获取的cookie`=`右面的内容

![03.png](/images/20200327181013/03.png)

## 完成

## 参考文献

[哔哩哔哩——腾讯掌控安全学院](https://www.bilibili.com/video/BV1vt41157Rj)

