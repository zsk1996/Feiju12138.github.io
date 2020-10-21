---
title: 【笔记】AJAX学习笔记
categories:
  - HTML/CSS/JS
date: 2020-05-25 16:03:45
---

## 前言

AJAX即“Asynchronous JavaScript and XML”（异步的JavaScript与XML技术），指的是一套综合了多项技术的浏览器端网页开发技术。Ajax的概念由杰西·詹姆士·贾瑞特所提出。（[维基百科](https://zh.wikipedia.org/wiki/AJAX)）

<!-- more -->

## 基本实现步骤

- 代码写在JavaScript代码域内

### 创建XMLHttpRequest对象

``` javascript
const xhr = new XMLHttpRequest();
```

### 设置xhr对象的事件监听函数

- 通过回调函数在合适的时候处理结果

``` javascript
xhr.onreadystatechange = function() {
    if(xhr.readyState == 4 && xhr.status == 200) {
        ...
    }
}
```

#### readyState状态码

|状态码|备注|
|---|---|
|0|未执行open函数|
|1|已执行open函数，未执行send函数|
|2|已执行send函数|
|3|正在接收服务器响应的数据|
|4|完成接收服务器响应的数据|

### 建立连接

- 第一个参数是请求类型
- 第二个参数是访问的资源地址
- 第三个参数为是不是异步

> `<src>`：资源地址

``` javascript
xhr.open("GET", "<src>", true);
```

### 发送请求

``` javascript
xhr.send(null);
```

## GET请求示例

``` javascript
const xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        ...
    }
};
// 在地址后拼接参数
xhr.open("GET", "/doCheck?name="+name.value, true);
xhr.send();
```

## POST请求示例

``` javascript
const xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        ...
    }
};
xhr.open("POST", "/doSave", true);
// Post请求传参需要设置请求头
xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
// 在括号内传递参数
xhr.send(name.value);
```

## 封装为函数

### GET请求

``` javascript
function doAjaxGet(url, params, callback) {
    const xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            callback(xhr.responseText);
        }
    };
    xhr.open("GET", `${url}?${params}`, true);
    xhr.send();
}
```

### POST请求

``` javascript
function doAjaxPost(url, params, callback) {
    const xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            callback(xhr.responseText);
        }
    };
    xhr.open("POST", url, true);
    // Post请求传参需要设置请求头
    xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
    xhr.send(params);
```

## 封装为框架

- 创建`ajax.js`文件

``` javascript
(() => {
    const ajax = function () {
    }
    ajax.prototype = {
        doAjaxGet: function (url, params, callback) {
            const xhr = new XMLHttpRequest();
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    callback(xhr.responseText);
                }
            };
            xhr.open("GET", `${url}?${params}`, true);
            xhr.send(null);
        }
        ,
        doAjaxPost: function (url, params, callback) {
            const xhr = new XMLHttpRequest();
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    callback(xhr.responseText);
                }
            };
            xhr.open("POST", url, true);
            // Post请求传参需要设置请求头
            xhr.setRequestHeader("Content-Type",
                "application/x-www-form-urlencoded");
            xhr.send(params);
        }
    }
    window.Ajax = new ajax();
})()
```

## 传参的几种方式

- 以Post请求方式为例

``` html
<input type="text" id="name"/>

<script>
let name = document.getElementById("name");
</script>
```

### 以字符串拼接传参

``` javascript
let params = "name="+name.value;
xhr.send(params);
```

### 以模版字符串传参

``` javascript
let params = `name=${name.value}`;
xhr.send(params);
```

### 以JS中的对象传参

- 原生JS通过对象传参可能会有问题

``` javascript
let params = {"name":name.value};
xhr.send(params);
```

## 关于浏览器兼容问题的解决

### 创建createXmlHttpRequest函数

- 创建createXmlHttpRequest函数用于不同浏览器创建不同XMLHttpRequest对象

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

### 通过createXmlHttpRequest函数创建XMLHttpRequest对象

``` javascript
const xhr = createXmlHttpRequest();
```

## 完成
