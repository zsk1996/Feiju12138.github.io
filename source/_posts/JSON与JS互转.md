---
title: 【笔记】JSON与JS互转
categories:
  - HTML/CSS/JS
date: 2020-10-03 10:30:00
---

## 前言

JSON与Javascript格式互转

<!-- more -->

## 互转

### JSON对象转换为Javascript字符串

> `<json>`：JSON对象

``` javascript
let js = JSON.parse(<json>);
```

### Javascript字符串转换为JSON对象

> `<js>`：JSON格式的JS字符串

``` javascript
let json = JSON.stringify(<js>)
```

## 完成

