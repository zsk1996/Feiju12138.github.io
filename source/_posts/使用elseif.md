---
title: 【代码】使用 else if
categories:
  - Swift Playgrounds
date: 2020-04-12 14:45:08
---

## 前言

关卡攻略

<!-- more -->

## 源代码

``` swift
for i in 1 ... 2 {
    moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    } else if isOnGem {
        collectGem()
    }
}
```

