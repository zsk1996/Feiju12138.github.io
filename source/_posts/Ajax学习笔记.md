---
title: 【笔记】Ajax学习笔记
categories:
  - HTML/CSS/JS
date: 2020-05-25 16:03:45
---

## 前言

AJAX即“Asynchronous JavaScript and XML”（异步的JavaScript与XML技术），指的是一套综合了多项技术的浏览器端网页开发技术。Ajax的概念由杰西·詹姆士·贾瑞特所提出。（[维基百科](https://zh.wikipedia.org/wiki/AJAX)）

<!-- more -->

## 基本实现步骤

- 代码写在JavaScript代码域内

### 创建XMLHTTPRequest对象

- 创建一个函数，用于创建对象并解决浏览器兼容问题

``` javascript
function createXmlHttpRequest() {
    // 针对谷歌、火狐等主流浏览器
    if(window.XMLHttpRequest) {
        return new XMLHttpRequest();
    }
    // 针对IE5、IE6浏览器
    else if(window.ActiveXObject) {
        return new ActiveXObject("Microsoft.XMLHTTP");
    }
    // 其他不支持Ajax的浏览器
    else {
        alert("您的浏览器不支持Ajax，请更换浏览器");
        return null;
    }
}
```

#### 创建对象

``` javascript
var xhr = createXmlHttpRequest();
```

### 准备发送请求

- 第一个参数是请求类型
- 第二个参数是访问的资源地址
- 第三个参数为是不是异步

> `<src>`：资源地址

``` javascript
xhr.open("GET", "<src>", true);
```

### 回调函数

- 在合适的时候处理结果

``` javascript
xhr.onreadystatechange = function() {
    if(xhr.readyState == 4 && xhr.status == 200) {
        ...
    }
}
```

### 发送请求

``` javascript
xhr.send();
```

## readyState状态码

|状态码|备注|
|---|---|
|0|未准备好|
|1|准备发送|
|2|发送请求|
|3|正在交互|
|4|交互完成|

## 未完待更

