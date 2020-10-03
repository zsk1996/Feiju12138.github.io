---
title: 【代码】Node创建简单的Web服务器
categories:
  - HTML/CSS/JS
date: 2020-09-24 22:53:07
---

## 前言

使用Nodejs，创建一个简单的Web服务器

<!-- more -->

## 源代码

- 创建`server.js`文件

### 正常访问

``` javascript
// 引入http模块
const http = require("http");
// 创建web服务器
const app = http.createServer();
// 设置端口
app.listen(80);
// 回调函数
app.on("request", function (req, res) {
    // 获取请求的URL和请求的方法
    console.log(req.url, req.method);

    // 200，正常访问
    res.writeHead(200, {
        "Content-Type": "text/html;charset=utf-8"
    });
    // 设置相应内容
    res.write("");
    // 结束并发送响应
    res.end();
});
```
### 异常访问

``` javascript
// 引入http模块
const http = require("http");
// 创建web服务器
const app = http.createServer();
// 设置端口
app.listen(80);
// 回调函数
app.on("request", function (req, res) {
    // 获取请求的URL和请求的方法
    console.log(req.url, req.method);

    // 404，异常访问
    res.writeHead(404);
    // 设置相应内容
    res.write("");
    // 结束并发送响应
    res.end();
});
```

### 重定向

``` javascript
// 引入http模块
const http = require("http");
// 创建web服务器
const app = http.createServer();
// 设置端口
app.listen(80);
// 回调函数
app.on("request", function (req, res) {
    // 获取请求的URL和请求的方法
    console.log(req.url, req.method);

    // 302，重定向
    res.writeHead(302, {
        Location: "https:feiju12138.github.io"
    });
    // 结束并发送响应
    res.end();
});
```

## 启动项目

``` sh
node server.js
```

## 完成

