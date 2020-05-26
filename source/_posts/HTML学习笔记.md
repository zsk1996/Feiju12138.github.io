---
title: 【笔记】HTML 学习笔记
date: 2019-11-28 22:05:16
tags:
categories:
- HTML/CSS/JS
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
<!DOCTYPE html>
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

## 属性

### 属性来修饰元素

- 属性的声明必须位于开始标记里

- 一个标签的属性可能不止一个，多个属性之间用空格隔开

- 多个属性之间不分先后顺序

### 每个属性都有值

- 属性和属性值之间用`=`连接

- 属性的值包含在引号中

### 标准属性

- 每个标签都有自己的特有属性

- 大多数标签都支持的属性称为标准属性

> `id=""`：编号
> `title=""`：标题
> `class=""`：类名
> `style=""`：样式

## 标签

### 文档标签

#### 文档声明标签

- html5中定义该文档是html文档

``` html
<!DOCTYPE html>
```

#### 文档的根标签

``` html
<html></html>
```

#### 头标签

``` html
<head></head>
```

##### 文档标题

``` html
<head>
    <title></title>
</head>
```

##### 元数据标签

- 元数据标签位于`head标签`内部，在`head标签`中承载的信息一般用户在浏览器中是访问不到的，但是对于搜索引擎，它们抓取网页的方式一般是集中关注网页`head标签`内容

###### 

> `charset="utf-8"`：网页字符集
> `name="keywords" content=""`：网页关键词
> `name="description" content=""`：网页描述
> `name="author" content=""`：网页作者
> `http-equiv="refresh" content="5; https://feiju12138.github.io"`：倒计时5秒自动跳转网页

``` html
<head>
    <meta>
</head>
```

#### 体标签

``` html
<body></body>
```

### 注释标签

``` html
<!-- 注释内容 -->
```

### 文本标签

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
<br>
```

#### 水平线标签

``` html
<hr>
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

#### 文本高亮

``` html
<mark></mark>
```

#### 字体标签

``` html
<font></font>
```

#### 文本居中

``` html
<center></center>
```

### 链接标签

> `href=""`：链接地址
> `href="#name/id"`：锚点链接
> `href="#"`：返回到本页
> `target=""`：窗口名称
> `title=""`：链接提示文字

``` html
<a></a>
```

### 图片标签

> 支持的格式：JPEG、PNG、GIF
> `src=""`：路径及名称
> `alt=""`：无效图片替代文本
> `width=""`：宽
> `height=""`：高

``` html
<img>
```

### 视频标签

> 支持的格式：MP4、OGG、WEBM
> `width=""`：宽
> `height=""`：高
> `controls`：显示控制

> `src=""`：路径及名称
> `type="video/mp4"`：类型

``` html
<video>
    <source>
</video>
```

### 音频标签

> 支持的格式：MP3、OGG、WAV
>
> > `controls`：显示控制

> `src=""`：路径及名称
> `type="audio/mp3"`：类型

``` html
<audio>
    <source>
</audio>
```

### 列表标签

#### 有序列表

> `type="a"`：使用小写字母排序
> `type="A"`：使用大写字母排序
> `type="1"`：使用数字排序
> `start="2"`：从2开始排序

``` html
<ol>
    <li></li>
</ol>
```

#### 无序列表

> `type="disc"`：实心圆
> `type="circle"`：空心圆
> `type="square"`：实心方块

``` html
<ul>
    <li></li>
</ul>
```

### 表格标签

#### 定义表格

> `width=""`：表格宽度
> `height=""`：表格高度
> `align=""`：表格位置
> `border=""`：表格边框
> `cellpadding=""`：单元格内边距
> `cellspacing=""`：单元格外边距
> `bgcolor=""`：表格背景颜色
> `background=""`：表格背景图片
> `bordercolor=""`：边框颜色

``` html
<table></table>
```

#### 定义行和列

> `colspan="2"`横向合并单元格（将两列单元格合并为一个）
> `rowspan="2"`纵向合并单元格（将两行单元格合并为一个）

``` html
<table>
    <tr>
        <td></td>
    </tr>
</table>
```

#### 定义表头

``` html
<table>
    <th></th>
</table>
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

### 块标签

``` html
<div></div>
<span></span>
```

### 表单标签

#### 定义表单

> `method="post"`：以post方式发送请求
> `method="get"`：以get方式发送请求

``` html
<form></form>
```

#### 表单项标签

> `type="text"`：文本框
> `type="password"`：密码框
>> `name=""`：名称
>> `value=""`：默认显示值
>> `maxlength=""`：限制输入的字符数
>> `readonly=""`只读模式

> `type="button"`：普通按钮
> `type="submin"`：提交按钮
> `type="reset"`：重置按钮
>> `name=""`：名称
>> `value=""`：默认显示值

> `type="radio"`：单选框
> `type="checkbox"`：复选框
>> `name=""`：设置名称，并用于分组。
>> `value=""`：默认显示值
>> `checked=""`：设置默认被选中

``` html
<input>
```

#### 下拉列表

> `name=""`：名称
> `size=""`：默认值1，如果大于1，则为滚动列表
> `multiple=""`：设置多选

> `value=""`选项的值
> `selected`：预选中

``` html
<select>
    <option></option>
</select>
```

#### 文本域

> `name=""`：名称
> `cols=""`：指定文本域的列数
> `rows=""`：指定文本域的行数
> `readonly=""`：只读模式

``` html
<textarea></textarea>
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

#### 中文拼音注释

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

#### 进度条

``` html
<progress value="50" max="100"></progress>
```

#### 文章或文档的节

``` html
<section></section>
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

### 浮动框架标签

> `src=""`：指向的链接
> `height=""`：高度
> `width=""`：宽度
> `frameborder=""`：边框

``` html
<iframe></iframe>
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

[达内教育](http://www.tedu.cn)
工单课堂
[哔哩哔哩——张奇MAX](https://www.bilibili.com/video/av70420291)
[简书——wade3po](https://www.jianshu.com/p/0abb613306c1)
[简书——hx永恒之恋](https://www.jianshu.com/p/2977a9f14afc)
[菜鸟笔记](https://www.runoob.com/html/html-formatting.html)

