---
title: 【笔记】JSON学习笔记
categories:
  - HTML/CSS/JS
date: 2020-09-19 17:58:55
---

## 前言

JSON（JavaScript Object Notation，JavaScript对象表示法，读作/ˈdʒeɪsən/）是一种由道格拉斯·克罗克福特构想和设计、轻量级的资料交换语言，该语言以易于让人阅读的文字为基础，用来传输由属性值或者序列性的值组成的数据对象。尽管JSON是JavaScript的一个子集，但JSON是独立于语言的文本格式，并且采用了类似于C语言家族的一些习惯。（[维基百科](https://zh.wikipedia.org/wiki/JSON)）

<!-- more -->

## 定义规则

- JSON的数据是由键值对构成的
- 多组数据由逗号分隔
- 键可以使用单引号定义，也可以使用双引号定义，还可以不使用引号定义

### 数据类型

- 数字（整数或浮点数）
- 字符串（通过双引号或单引号定义）
- 布尔值（true或false）
- 数组（通过方括号定义）
- 对象（通过花括号定义）

### 定义数据

> `<key>`键

#### 数字

``` json
{"<key>":1}
```

#### 字符串

``` json
{"<key>":"str"}
```

#### 布尔值

``` json
{"<key>":true}
```

#### 数组

``` json
{
    "<key>":[
        {},{}
    ]
}
```

#### 对象

``` json
{
    "<key>":{
        "":""
    }
}
```

## 获取数据

``` json
json对象.键名

json对象["键名"]
```

## 遍历JSON对象

``` javascript
for (var key in persion) {
    console.log(key+":"+persion[key]);
}
```

## 参考文献

[哔哩哔哩——黎曼的猜想](https://www.bilibili.com/video/BV1uJ411k7wy)
