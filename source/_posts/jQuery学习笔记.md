---
title: 【笔记】jQuery 学习笔记
date: 2019-11-22 13:55:21
tags:
categories:
- HTML/CSS/JS
---

## 前言

jQuery学习笔记

<!-- more -->

## jQuery基础

### 下载的版本

- jquery-3.3.1.min.js
压缩版（发布版）

- jquery-3.3.1.js
常规版（开发版）

### 开发工具

- [HBuilder](https://dcloud.io)、[WebStrom](https://www.jetbrains.com/webstorm/)、[Dreamweaver](https://www.adobe.com/cn/products/dreamweaver.html)、[IDEA](https://www.jetbrains.com/idea/)

### 预加载函数

- 写在`<script></script>`标签内，如果写在`<head></head>`标签内需要预加载函数

#### 第一种写法

``` javascript
<head>
    <script type="text/javascript" src="js/jquery-3.4.1.js"></script>
    <script>
        jQuery(document).ready(function(){
            ...
        });
    </script>
</head>
```

#### 第二种写法

``` javascript
<head>
    <script type="text/javascript" src="js/jquery-3.4.1.js"></script>
    <script>
        $(document).ready(function(){
            ...
        });
    </script>
</head>
```

#### 第三种写法

``` javascript
<head>
    <script type="text/javascript" src="js/jquery-3.4.1.js"></script>
    <script>
        jQuery(function(){
            ...
        });
    </script>
</head>
```

#### 第四种写法

``` javascript
<head>
    <script type="text/javascript" src="js/jquery-3.4.1.js"></script>
    <script>
        $(function(){
            ...
        });
    </script>
</head>
```

### Dom对象和jquery对象的转换

- Dom对象->jquery对象

``` javascript
$(Dom对象)
```

- jquery对象->Dom对象

``` javascript
jquery对象[0]
jquery对象.get(0)
```

## jQuery选择器\*

### 基本选择器

- 标签选择器

``` javascript
$("标签名")
```

- 类选择器（.）

``` javascript
$(".class值")
```

- id选择器（#）

``` javascript
$("#id值")
```

- 并集选择器（,）

``` javascript
$(".class值, #id值")
```

- 交集选择器（相连）

``` javascript
$(".class值#id值")
```

- 全局选择器（\*）

``` javascript
$("*")
```

### 层次选择器

- 相邻选择器（+）
只选后面的

``` javascript
$("选择器1+选择器2")
```

- 同辈选择器（~）
只选后面的

``` javascript
$("选择器1~选择器2")
```

- 后代选择器（空格）

``` javascript
$("选择器1 选择器2")
```

- 子代选择器（>）

``` javascript
$("选择器1>选择器2")
```

#### 兄弟选择器

> `example`

- 选中id为example的元素`后面紧邻`的span兄弟元素

``` javascript
$("#example").next("span")
```

- 选中id为example的元素`前面紧邻`的span兄弟元素

``` javascript
$("#example").prev("span")
```

- 选中id为example的元素`后面所有`的span兄弟元素

``` javascript
$("#example").nextAll("span")
```

- 选中id为example的元素`前面所有`的span兄弟元素

``` javascript
$("#example").prevAll("span")
```

- 选中id为example的元素`前后所有`的span兄弟元素

``` javascript
$("#example").siblings("span")
```

### 属性选择器（[...]）

- $("[属性名]")

``` javascript
//选中全部元素中，有class属性的元素
$("[class]")
```

- $("[属性名=属性值]")

``` javascript
$("[class=xxx]")
$("[class="xxx"]")
```

- $("[属性名!=属性值]")

``` javascript
//有class但值不是a，或没有class
$("[class!=a]")
```

- $("[属性名^=属性值]")

``` javascript
//class以a开头的元素
$("[class^=a]")
```

- $("[属性名$=属性值]")

``` javascript
//class以a结尾的元素
$("[class$=a]")
```

- $("[属性名\*=属性值]")

``` javascript
//class有a的元素
$("[class*=a]")
```

### 过滤选择器（:）

- 最开头那一个

``` javascript
:first
```

- 最后那一个

``` javascript
:last
```

- 偶数

``` javascript
:even
```

- 奇数

``` javascript
:odd
```

- 第index个

``` javascript
:eq(index)
```

- 大于index的全部元素

``` javascript
:gt(index)
```

- 小于index的全部元素

``` javascript
:lt(index)
```

- 除了...以外的

``` javascript
:not(选择器)
```

- 选中所有的标题元素

``` javascript
:header
```

- 获取当前焦点的元素

``` javascript
:focus
```

### 可见性选择器

- 选中所有可见的元素

``` javascript
:visible
```

- 选中所有隐藏的元素

``` javascript
:hidden
```

## jQuery事件

``` javascript
$(document).ready(function(){
    $(选择器).事件类型(function(){
        ...
    });
});
```

### windows事件

``` javascript
ready();
```

#### 鼠标事件

- 单击事件

``` javascript
click();
```

- 鼠标悬浮

``` javascript
mouseover();
```

- 鼠标离开

``` javascript
mouseout();
```

#### 键盘事件

- 按键（从上往下的过程）

``` javascript
keydown();
```

- 按键（被压到最底部）

``` javascript
keypress();
```

- 松开按键

``` javascript
keyup();
```

- 通过`event.keyCode`指定具体的按键

``` javascript
$("body").keydown(function(event){
    if(event.keyCode == 13){
        alert("回车");
    }
});
```

### 表单事件

- 获取焦点

``` javascript
focus();
```

- 失去焦点

``` javascript
blur();
```

### 绑定事件与移除事件

``` javascript
$(...).click(function(){
    ...
});
```

- 绑定事件

``` javascript
$(...).bind("事件名", [数据], 函数);
```

- 批量绑定

``` javascript
$(...).bind({
    "事件名":函数,
    "事件名":函数,
    ...
});
```

- 移除事件

``` javascript
$(...).unbind("事件名");
```

### 复合事件

#### 切换使用`mouseover()`和`mouseout()`

``` javascript
hover(function1, function2);
```

#### 多个`click()`事件

``` javascript
toggle(function1, function2, ...);
```

`toggle()`还有其他含义（隐藏与显示）

#### 隐藏与显示

``` javascript
hide([速度], [回调函数]);
```

- 隐藏

``` javascript
hide();
```

- 显示

``` javascript
show();
```

- 切换隐藏与显示

``` javascript
toggle();
slideToggle();
```

##### 淡入淡出（透明度）

- 淡入（显示）

``` javascript
fadeIn();
```

- 淡出（隐藏）

``` javascript
fadeOut();
```

##### 控制高度

- 下拉(显示)

``` javascript
slideDown();
```

- 上拉（隐藏）

``` javascript
slideUp();
```

## 操作DOM

### 样式操作

- 设置css()

``` javascript
jquery对象.css("属性名", "属性值");
jquery对象.css({
    "属性名":"属性值",
    "属性名":"属性值",
    ...
})
```

- 追加或移除样式class

``` javascript
addClass("x");
addClass("x x x");
removeClass(x);
removeClass(x x);
//移除全部样式
removeClass();
//切换追加与移除
toggleClass("x x x");
```

### 内容操作

- 获取或修改值（包括标签）

``` javascript
html();
html(xxx);
```

- 获取或修改值（仅文本）

``` javascript
text();
text(xxx);
```

- 获取或修改value值

``` javascript
val();
val(xxx);
```

### 节点与属性操作

#### 节点操作

##### 查询节点

``` javascript
(jquery选择器)
```

##### 创建节点

``` javascript
$div = $(<div></div>);
```

##### 插入节点

###### 内部插入

- 将B追加到A中（首）

``` javascript
$(A).append(B);
$(B).appendTo(A);
```

- 将B追加到A中（尾）

``` javascript
$(A).prepend(B);
$(B).prependTo(A);
```

###### 外部插入

- 将B插入到A后

``` javascript
$(A).after(B);
$(B).insertAfter(A);
```

- 将B插入到A前

``` javascript
$(A).before(B);
$(B).insertBefore(A);
```

##### 替换节点

- 将B替换到A

``` javascript
$A.replaceWith($B);
$B.replaceAll($A);
```

##### 删除节点

- 彻底删除

``` javascript
remove();
```

- 将节点删除，但关联的事件、数据不会删除

``` javascript
datech();
```

- 只删除内容

``` javascript
empty();
```

##### 克隆节点

- 克隆节点和相关事件

``` javascript
clone(true);
```

- 只克隆节点，不克隆事件

``` javascript
clone(false);
```

#### 属性操作

- 获取属性值

``` javascript
attr("属性名");
```

- 设置属性值

``` javascript
attr("属性名", "属性值");
attr({
    "属性名":"属性值",
    "属性名":"属性值",
    ...
})
```

- 删除属性值

``` javascript
removeAttr("属性名");
```

##### jquery1.6新特性

- 获取属性值

``` javascript
prop("属性名");
```

- 修改属性值

- 设置属性值

``` javascript
prop("属性名", "属性值");
prop({
    "属性名":"属性值",
    "属性名":"属性值",
    ...
})
```

##### attr()和prop()的区别

- `attr()`函数在jquery1.6之前就有，对自定义属性的操作，使用`attr()`函数
- `prop()`函数在query1.6之后新引进，对固有属性的操作，使用`prop()`函数

### 获取集合与遍历集合

#### 子节点集合

``` javascript
$(...).children(...);
$(...).children();
```

#### 后代集合

``` javascript
$(...).find(...);
$(...).find();
```

#### 同辈集合

- 后一个

``` javascript
next();
```

- 前一个

``` javascript
prev();
```

- 同辈

``` javascript
siblings();
```

#### 前辈集合

- 父代

``` javascript
parent();
```

- 祖先

``` javascript
parents();
```

#### 过滤集合

- 很多方法的"()"就是一个过滤选择器

``` javascript
filter("选择器");
```

#### 遍历集合

``` javascript
$(...).each(function(index, element){
    ...
});
```

## CSS-Dom操作

- 高

``` javascript
height();
height(xxx);
```

- 宽

``` javascript
width();
width(xxx);
```

- 偏移量

``` javascript
offset();
offset(function(index, oldOffset){
    var newOffset.left = new Object();
    newOffset.left = oldOffset.left+100;
    newOffset.right = oldOffset.right+100;
};
```

- 获取已定位的最近的祖先元素

``` javascript
offsetParent();
```

- 滚动条水平定位

``` javascript
scrollLet();
```

- 滚动条垂直定位

``` javascript
scrollTop();
```

## 表单校验

- 当失去焦点时触发

``` javascript
blur(function(){});
```

- 当点击按钮时触发

通过返回的布尔值，告知程序是否校验成功，决定表单是否跳转

``` javascript
submit(function(){});
```

- 正则表达式

返回布尔值

``` javascript
正则表达式.test(xxx);
```

## 表单选择器

### 匹配所有"input"、"textarea"、"select"、"button"

``` javascript
:input
$(":input").each(function(index, elemet){
    if(index==0){
    }else if(index==1){
    }
});
```

### 匹配所有单行文本框

``` javascript
:text
```

### 匹配所有密码框

``` javascript
:password
```

### 匹配所有单选按钮

``` javascript
:radio
```

### 匹配所有复选框

``` javascript
:checkbox
```

### 匹配所有提交按钮

``` javascript
:submit
```

### 匹配所有图像

``` javascript
:image
```

### 匹配所有重置按钮

``` javascript
:reset
```

### 匹配所有按钮

``` javascript
:button
```

### 匹配所有文件域

``` javascript
:file
```

### 匹配所有不可见元素

``` javascript
:hidden
```

## 参考文献

[哔哩哔哩——DT课堂原名颜群](https://www.bilibili.com/video/av53943392)

