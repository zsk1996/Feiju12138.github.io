---
title: 【代码】创建更巧妙的While循环
categories:
  - Swift Playgrounds
date: 2020-04-12 19:58:36
---

## 前言

关卡攻略

<!-- more -->

## 源代码

``` swift
while !isBlocked {
    if isOnClosedSwitch {
        toggleSwitch()
    }
    moveForward()
}
```

