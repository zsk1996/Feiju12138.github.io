---
title: 【笔记】HTML 学习笔记
date: 2019-11-28 22:05:16
tags:
categories:
- H5/CSS/JS
---

## 前言

超文本标记语言是一种用于创建网页的标准标记语言。HTML是一种基础技术，常与CSS、JavaScript一起被众多网站用于设计网页、网页应用程序以及移动应用程序的用户界面。网页浏览器可以读取HTML文件，并将其渲染成可视化网页。HTML描述了一个网站的结构语义随着线索的呈现，使之成为一种标记语言而非编程语言。[维基百科](https://zh.wikipedia.org/wiki/HTML)

<!-- more -->

## 语法

- html文档后缀名

> .html
> .htm

- 标签分为

双标签：有开始标签和结束标签
单标签：开始标签和结束标签在一起

- 标签可以嵌套

- 在开始标签中可以定义属性，属性是由键值对构成，值需要用引号引起来

- html的标签不区分大小写，但是建议使用小写

## 代码

``` html
<!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
        <p>Hello World !</p>
    </body>
</html>
```

## 标签

### 文档标签

- 构成html最基本的标签

#### 文档的根标签

``` html
<html></html>
```

#### 头标签

- 用于指定html文档的一些属性，引入外部资源

``` html
<head></head>
```

#### 文档标题

``` html
<title></title>
```

#### 体标签

``` html
<body></body>
```

#### \<!DOCTYPE html>

- html5中定义该文档是html文档

### 文本标签

#### 注释

``` html
<!-- 注释内容 -->
```

#### 标题标签

``` html
<h1></h1>
<h2></h2>
<h3></h3>
<h4></h4>
<h5></h5>
<h6></h6>
```

#### 段落标签

``` html
<p></p>
```

#### 换行标签

``` html
<br/>
```

#### 水平线标签

``` html
<hr/>
```

#### 字体加粗

``` html
<b></b>
<strong></strong>
```

#### 字体斜体

``` html
<i></i>
<em></em>
```

#### 字体下划线

``` html
<u></u>
```

#### 字体删除线

``` html
<s></s>
<del></del>
```

#### 文字上标

``` html
<sub></sub>
```

#### 文字下标

``` html
<sup></sup>
```

#### 插入字

``` html
<ins></ins>
```

#### 字体标签

``` html
<font></font>
```

#### 文本居中

``` html
<center></center>
```

### 图片标签

``` html
<img src="#"/>
```

### 列表标签

#### 有序列表

``` html
<ul>
    <li></li>
</ul>
```

#### 无序列表

``` html
<ol>
    <li></li>
</ol>
```

### 链接标签

``` html
<a href="#"></a>
```

### 块标签

``` html
<div></div>
<span></span>
```

### 语义化标签

#### 页眉

``` html
<header></header>
```

#### 页脚

``` html
<footer></footer>
```

#### 导航栏标签

``` html
<nav></nav>
```

#### 独立内容区域

``` html
<article></article>
```

#### 页面侧边栏

``` html
<aside></aside>
```

#### 时间标签

``` html
<time></time>
```

#### 注释标签

> `rt`：在上方的注释
> `rp`：隐藏的注释

``` html
<ruby>
    张<rt>Zhang</rt><rp>不显示</rp>
</ruby>
```

#### 点击展开详情

``` html
<details>
    <summary>更多</summary>
    <p>详细内容<p>
</details>
```

#### 给字段添加背景色

``` html
<mark></mark>
```

#### 进度条

``` html
<progress value="50" max="100"></progress>
```

#### 文章或文档的节

``` html
<section></section>
```

#### 视频

``` html
<video></video>
```

#### 音频

``` html
<audio></audio>
```

#### 模糊查询

``` html
<input type="text" list="test">
<datalist id="test">
    <option value="test1"></option>
    <option value="test2"></option>
</datalist>
```

#### 多媒体

``` html
<embed></embed>
```

#### 画布

``` html
<canvas></canvas>
```

#### 主要内容

``` html
<main></main>
```

### 表格标签

#### 定义表格

``` html
<table></table>
```

#### 定义行

``` html
<tr></tr>
```

#### 定义列

``` html
<td></td>
```

#### 定义表头

``` html
<th></th>
```

#### 表格标题

``` html
<capital></capital>
```

#### 表格头标签

``` html
<thead></thead>
```

#### 表格体标签

``` html
<tbody></tbody>
```

#### 表格脚标签

``` html
<tfoot></tfoot>
```

### 表单标签

#### 定义表单

``` html
<form></form>
```

#### 表单项标签

##### 文本

``` html
<input type="text"/>
```

##### 密码输入框

``` html
<input type="password"/>
```

##### 单选框

``` html
<input type="radio"/>
```

##### 复选框

``` html
<input type="checkbox"/>
```

##### 按钮

``` html
<input type="button"/>
```

#### 下拉列表

``` html
<select></select>
```

#### 文本域

``` html
<textarea></textarea>
```

### "计算机输出"标签

#### 定义计算机代码

``` html
<code></code>
```

#### 定义键盘码

``` html
<kbd></kbd>
```

#### 定义计算机代码样本

``` html
<samp></samp>
```

#### 定义变量

``` html
<var></var>
```

#### 定义预格式文本

``` html
<pre></pre>
```

### 引文、引用

#### 定义缩写

``` html
<abbr></abbr>
```

#### 定义地址

``` html
<address></address>
```

#### 定义文字方向

``` html
<bdo></bdo>
```

#### 定义长的引用

``` html
<blockquote></blockquote>
```

#### 定义短的引用

``` html
<q><q>
```

#### 定义引用、引证

``` html
<cite></cite>
```

#### 定义项目

``` html
<dfn></dfn>
```

## 参考文献

[哔哩哔哩——张奇MAX](https://www.bilibili.com/video/av70420291)
[简书——wade3po](https://www.jianshu.com/p/0abb613306c1)
[菜鸟笔记](https://www.runoob.com/html/html-formatting.html)

