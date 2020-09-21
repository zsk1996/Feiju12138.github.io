---
title: 【代码】jQuery实现AJAX
categories:
  - HTML/CSS/JS
date: 2020-09-05 14:48:48
---

## 前言

jQuery实现AJAX，将响应结果返回到前端页面

<!-- more -->

## get函数

``` javascript
//1.请求url
var url = "/jquery/doAjaxGet";
//2.请求参数
var params = "name=zhangsan";
//3.发送异步请求
$.get(url, params, (result) => {
    $("#resultId").html(result);
});
```

## post函数

``` javascript
//1.请求url
var url = "/jquery/doAjaxPost";
//2.请求参数
var params = "name=zhangsan";
//3.发送异步请求
$.post(url, params, (result) => {
    $("#resultId").html(result);
});
```

## ajax函数

``` javascript
//1.请求url
let url = "/jquery/doAjaxPost";
//2.请求参数
let params = "name=zhangsan";
//3.发送异步请求
$.ajax({
    // 可以省略（默认为GET请求）
    type: "POST",
    url: url,
    // 可以省略（如果无需向服务端传递参数）
    data: params,
    // 可以省略（由ajax函数内部基于返回值进行匹配处理）
    dataType: "text",
    // 可以省略（默认为true，表示异步）
    async: true,
    // 处理服务端返回的正常信息
    success: function (result) {
        $("#resultId").html(result);
    },
    // 处理服务端返回的异常信息
    error: function (result) {
        console.log(xhr.statusText);
        $("#resultId").html(xhr.statusText);
    }
});
```

## load函数

- load会将响应直接返回到指定位置

``` javascript
//1.请求url
var url = "/jquery/doAjaxGet";
//2.请求参数
var params = "msg=hello jquery ajax get method";
//3.发送异步请求，直接返回响应
$("#resultId").load(url, params);
```

## 完成
