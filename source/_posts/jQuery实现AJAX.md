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

> `<url>`：请求的url地址
> `<params>`：请求的参数
> `(result) => {...}`：回调函数，它是匿名函数，可以写成箭头函数
> `<dataType>`：指定响应的数据类型。理论上可以省略，因为jQuery实现的ajax会自动识别


``` javascript
$.get("<url>", "<params>", (result) => {
    $("#resultId").html(result);
}, "<dataType>");
```

### getJSON函数

``` javascript
$.getJSON("<url>", "<params>", (result) => {
    $("#resultId").html(result);
});
```

## post函数

``` javascript
$.post("<url>", "<params>", (result) => {
    $("#resultId").html(result);
}, "<dataType>");
```

## ajax函数

> `type`：标准写法type的值应该大写

``` javascript
$.ajax({
    // 可以省略（默认为GET请求）
    type: "POST",
    url: "<url>",
    // 可以省略
    contentType: "application/json;charset=utf-8",
    // 可以省略（如果无需向服务端传递参数）
    data: "<params>",
    // 可以省略（由ajax函数内部基于返回值进行匹配处理）
    // 常见参数：html、xml、json、jsonp（跨域）
    dataType: "text",
    // 可以省略（默认为true，表示异步）
    async: true,
    // 处理服务端返回的正常信息
    success: function (result) {
        $("#resultId").html(result);
    },
    // 处理服务端返回的异常信息
    error: function (xhr) {
        console.log(xhr.statusText);
        $("#resultId").html(xhr.statusText);
    }
});
```

### 另一种方式

``` javascript
$.ajax({
    type: "DELETE",
    url: url
})
// 处理成功信息
.done(function(result){
    ...
})
// 处理失败信息
.fail(function(){
    ...
})
// 无论成功或失败都执行
.always(function(){
    ...
});
```

## load函数

- load会将响应直接返回到指定位置

``` javascript
$("#resultId").load("<url>", "<params>");
```

## 完成

## 参考文献

[间书——涎涎](https://www.jianshu.com/p/b36481c4f3c9)

