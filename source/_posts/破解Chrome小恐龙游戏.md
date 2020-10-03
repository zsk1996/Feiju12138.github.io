---
title: 【骚操作】破解Chrome小恐龙游戏
categories:
  - HTML/CSS/JS
date: 2020-09-28 19:17:13
---

## 前言

通过在Chrome控制台修改Javascript代码，破解小恐龙游戏（[chrome://dino](chrome://dino/)），实现无敌和加速

<!-- more -->

## 无敌

- 将内置的`gameOver`条件从原来的判定函数改为空函数

``` javascript
Runner.prototype.gameOver = function(){}
```

## 加速

- 通过使用内置的`setSpeed()`函数修改速率

> `<num>`：速率值

``` javascript
Runner.instance_.setSpeed(<num>)
```

## 完成

## 参考文献

[小志知识库](https://xiaozhizsk.baklib.com/16e5/25d7)

