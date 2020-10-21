---
title: 【笔记】Javascript  学习笔记
categories:
  - HTML/CSS/JS
date: 2020-07-31 17:22:01
---

## 前言

JavaScript（通常缩写为JS）是一种高级的、解释型的编程语言。JavaScript是一门基于原型、函数先行的语言，是一门多范式的语言，它支持面向对象编程，命令式编程，以及函数式编程。它提供语法来操控文本、数组、日期以及正则表达式等，不支持I/O，比如网络、存储和图形等，但这些都可以由它的宿主环境提供支持。它已经由ECMA（欧洲电脑制造商协会）通过ECMAScript实现语言的标准化。它被世界上的绝大多数网站所使用，也被世界主流浏览器（Chrome、IE、Firefox、Safari、Opera）支持。（[维基百科](https://zh.wikipedia.org/wiki/JavaScript)）

<!-- more -->

## 书写位置

### script标签内

``` javascript
<script>
    ...
</script>
```

### 引入.js文件

> `<<src>>`：路径.js文件路径

``` javascript
<head>
    <script src="<<src>>"></script>
</head>
```

### 当触发事件时执行指定函数

``` java
<body>
    <input type="button" onclick="">
</body>
```

## 注释

- 和java语法完全相同

``` javascript
// 单行注释

/* 多行注释 */
```

## 打印字符串

### 打印到弹窗

> `<<variable>>`：变量

``` javascript
alert(<<variable>>);
```

### 打印到控制台

``` javascript
console.log(<<variable>>);
```

#### 在控制台打印对象结构

``` javascript
console.dir(<<variable>>);
```

### 直接打印到网页上

``` javascript
document.write(<<variable>>);
```

## 声明变量

- var可以声明任何类型变量，一个变量一可以赋值任何数据类型

> `<<name>>`变量名

``` javascript
var <<name>> = <<variable>>;
```

### 变量（ES6新特性）

``` javascript
let <<name>> = <<variable>>;
```

### 常量（ES6新特性）

``` javascript
const <<name>> = <<variable>>;
```

### var和let、const 的区别

- let和const都是es5，es6新版本的js语言规范出来的定义，在这以前定义一个变量只能用var。let和const都是为了弥补var的一些缺陷而新设计出来的。

## 数据类型

- 基本数据类型
String Number Boolean Null Undefined
- 引用数据类型
Object

### 检查当前数据类型

``` javascript
typeof(<<variable>>);
```

### string字符串

- - 在JS中字符串需要使用引号引起来
- 使用双引号或单引号都可以，但是不要混着用
- 引号不能嵌套，双引号不能放单引号，单引号不能放双引号
- 使用typeof检查字符串时，会返回string

### Number数值型

- 在JS中所有的数值都是Number类型
- 包括整数和浮点数
- 使用typeof检查数值时，会返回number

#### 最值

``` javascript
Number.MAX_VALUE
```

- 如果使用Number表示的数字超过了最大值，则会返回一个`Infinity` （表示正无穷）
- 如果使用Number表示的数字低于了最小值，则会返回一个`-Infinity` （表示负无穷）
- 使用typeof检查Infinity也会返回Number

- 在JS中整数的运算基本可以保证精确
- 如果使用JS进行浮点运算，可能得到一个不精确的结果，所以千万不要使用JS进行对精确度要求比较高的运算

### boolean类型

- 布尔值只有两个，主要用来做逻辑判断
- `true`表示真，`false`表示假
- 使用typeof检查一个布尔值时，会返回boolean

### Null类型

- Null（空值）类型的值专门用来表示一个为空的对象
- 使用typeof检查一个null值时，会返回object

### Undefined类型

- Undefined（未定义）类型的值只有一个就是undefined
- 当声明一个变量，但是并不给变量赋值时，它的值就是undefined
- 使用typeof检查一个undefined值时，会返回undefined

### 强制类型转换

- 指将一个数据类型强制转换为其他的数据类型
- 类型转换主要是指，将其他的数据类型，转化为String、Number、Boolean

#### 将其他数据类型转换为String

#####  toString

- 调用被转换数据类型的toString()方法
- 该方法不会影响到原变量，他会将转换的结果返回
- 但是注意：null和undefined这两个值没有toString()方法，如果调用他们的方法，会报错

##### String()

- 调用String()函数，并将被转换的数据作为参数传递给函数
- 使用String()函数做强制类型转换时，
- 对于Number和Boolean实际上就是调用的toString()方法
- 但是对于null和undefined，就不会调用toString()方法
- 它会将null直接转换为"null"，将undefined直接转换为"undefined"

#### 将其他的数据类型转换为Number

##### Number()

###### 字符串转换为数字

- 如果是纯数字的字符串，则直接将其转化为数字
- 如果字符串中有非数字的内容，则转换为NaN
- 如果字符串是一个空串或者是一个全是空格的字符串，则转换为0

###### 布尔值转换为数字

- true 转成 1
- false 转成 0

###### Null转换为数字

- 结果为0

###### undefined转换为数字

- 结果为NaN

##### parseInt()

- parseInt()函数：把一个字符串转换为一个整数
- parseInt()可以将一个字符串中的有效的整数内容取出来

- parseFloat()函数：把一个字符串转换为一个浮点数
- parseFloat()作用和parseInt()类似，不同的是它可以获取有效的小数

- 如果对非String使用parseInt()或parseFloat()，它会先将其转换为String，然后再操作

#### 其他的数据类型转换为Boolean

- 使用Boolean()函数
- 数字 转换为 布尔值， 除了0和NaN，其余的都是true
- 字符串转换为布尔值，除了空串，其余的都是true
- null和undefind都会转换为false

### 其他

- 在js中，如果需要使用16进制的数字，则需要以0x开头
- 如果需要表示8进制数字，则需要以0开头
- 如果需要表示2进制的数字，则需要以0b开头
- 但不是所有浏览器都支持

## 运算符

> 算术运算符： +，-，\*，/，%，++，--
> 赋值运算符： =，+=，-=，\*=，/=，%=
> 比较运算符： ==，!=，>，>=，<，<=
> 位运算符： & ， |
> 逻辑运算符： && ，||   ( false && 表达式, true || 表达式 )
> 前置逻辑运算符： ! (not)
> 三元运算符： 表达式 ? 表达式 : 表达式

## 数组

- JS中的数组可以存储任意类型的数据
- JS中的数组长度是可以被任意改变的

### 声明数组

``` javascript
var arr = [];

var arr = ["Hello", 111, false, new Object()];

var arr = new Array();

var arr = new Array("Hello", 111, false, new Object());
```

## 对象

### 对象的分类

#### 内建对象

- 由ES标准定义的对象，在任何的ES的实现中都可以使用
- 比如：Math String Number Boolean Function Object

#### 宿主对象

- 由JS的运行环境提供的对象，目的主要指由浏览器提供的对象
- 比如BOM DOM

#### 自定义对象

- 由开发人员自己创建的对象

### 创建对象

#### 创建对象时定义属性

``` javascript
var obj = {"name":"zhangsan", "sex":"male"};

var obj = {name:"zhangsan", sex:"male"};
```

#### 创建对象后定义属性

``` javascript
var obj = new object();
obj.name = "zhangsan";
obj.sex = "male";
```

#### 通过构造函数创建对象

``` javascript
function fun(name, sex) {
    this.name = name;
    this.sex = sex;
}
var obj = fun("zhangsan", "male")
```

### 属性

- 在对象中保存的值称为属性

#### 向对象添加属性

``` javascript
对象.属性名 = 属性值;
```

#### 读取对象中的属性

``` javascript
对象.属性名
```
- 如果读取对象中没有的属性值，不会报错而是会返回undefined

#### 修改对象的属性值

``` javascript
对象.属性名 = 属性值;
```

#### 删除对象的属性

``` javascript
delete 对象.属性名
```

### 属性名

- 对象的属性名不强制要求遵守标识符的规范，什么乱七八糟的名字都可以使用
- 但是我们使用时还是尽量按照标识符的规范去做
- 如果要使用特殊的属性名，不能采用.的方式来操作，需要使用另一种方式

``` javascript
对象['属性名'] = 属性值;
```

- 读取时也需要采用这种方式
- 使用[]这种形式去操作属性，更加的灵活，
- 在[]中可以直接传递一个变量，这样变量值是多少就会读取那个属性

### 属性值

- JS对象的属性值，可以是任意的数据类型，甚至也可以是一个对象

### in运算符

- 通过该运算符，可以检查一个对象中是否含有指定的属性，如果有则返回true，没有则返回false

``` javascript
"属性名" in 对象
```

### 继承关系

- 在构造函数的对象通过prototype关键字添加公有属性，通过构造函数创建的对象也能访问到这个属性

``` javascript
function point(x, y) {
    this.x = x;
    this.y = y;
}

var a = new point(10, 20);

// 通过prototype关键字在构造函数添加公有属性z
point.prototype.z = 30;

// 虽然对象a中并没有属性z
console.dir(a);

// 但此时对象a也能访问构造函数的公有属性
console.log(a.z);
```

``` javascript
a.__proto__==point.prototype;
```

### 其他

- JS中的变量都是保存到栈内存中的，
- 基本数据类型的值直接在栈内存中存储
- 值与值之间是独立存在，修改一个变量不会影响其他的变量

- 对象是保存到堆内存中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间
- 而变量保存的是对象的内存地址（对象的引用），如果两个变量保存的是用一个对象的引用，
- 当一个通过一个变量修改属性时，另一个也会受到影响

- 当比较两个基本数据类型的值时，就是比较值。
- 而比较两个引用数据类型时，它是比较的对象的内存地址，
- 如果两个对象是一模一样的，但是地址不同，它也会返回false

- 使用对象字面量，可以在创建对象时，直接指定对象中的属性

``` javascript
{属性名:属性值, 属性名:属性值……}
```

- 属性名和属性值时一组一组的名值对结构，
- 名和值之间使用`:`连接，多个名值对之间使用`,`隔开，如果一个属性之后没有其他属性了，就不要写`,`

## 函数

- 函数也是一个对象
- 函数中可以封装一些功能（代码），在需要时可以执行这些功能（代码）
- 函数中可以保存一些代码在需要的时候调用
- 使用typeof检查一个函数对象时，会返回function

- 我们在实际开发中很少使用构造函数来创建一个函数对象
- 创建一个函数，可以将要封装的代码以字符串的形式传递给构造函数

- 封装到函数中的代码不会立即执行，函数中的代码会在函数调用的时候执行

### 创建函数

#### 使用函数声明来创建一个函数

``` javascript
function 函数名(参数列表){
    ...
}
```

#### 使用函数表达式来创建一个函数

``` javascript
var 函数名 = function (参数列表){
    ...
}
```

#### 箭头函数

``` javascript
var 函数名 = (参数列表)=>{
    ...
}
```

#### 底层创建函数

``` javascript
var 函数名 = new Function('a','b','return a+b');
```

### 匿名函数及自调用

``` javascript
(function(参数列表){
    ...
})(参数列表);

(function(参数列表){
    ...
}(参数列表));
```

### 调用函数

``` javascript
函数名()
```

- 当调用函数时，函数中封装的代码会按照顺序执行

### 预加载函数

- function函数会在浏览器加载完整网页后立即执行

``` javascript
window.onload = function(){
    ...
}
```

### 构造函数

``` javascript
let point = function(x,y) {
    this.x = x;
    this.y = y;
}
```

#### ES6新特性

``` javascript
class point {
    constructor(x,y) {
        this.x = x;
        this.y = y;
    }
    toStr() {
        console.log(this.x,this.y);
    }
}
```

#### 使用构造函数创建对象

``` javascript
var 对象名 = new point(10,20);
```

### 其他

- 在调用函数时，可以在()中指定实参(实际参数)，实际参数会赋值给函数中对应的形参

- 调用函数时解析器不会检查实参的类型，所以要注意，是否有可能会接收到非法的参数，如果有可能则对参数进行类型的检查
- 函数的实参可以是任意的数据类型

- 调用函数时，解析器也不会检查实参的数量，多余实参不会被赋值
- 如果实参的数量少于形参的数量，则没有对应实参的形参将是undefined

### 返回值

可以使用return来设置函数的返回值

``` javascript
return 值;
```

- return后的值将会作为函数的执行结果返回，可以定义一个变量来接收该结果
- 在函数中return后的语句都不会执行

## 判断语句

### if判断语句

- 和java语法完全相同

> `<<boolean>>`：结果为布尔值的语句

``` javascript
if (<<boolean>>) {
    ...
}
```

### seitch判断语句

- 和java语法完全相同

> `<<num>>`：数值

``` javascript
switch (<<variable>>) {
    case <<num>> :
        ...
        break;
    default :
        ...
        break;
}
```

## 循环语句

### while循环语句

- 和java语法完全相同

``` javascript
while (<<boolean>>) {
    ...
}
```

### for循环语句

- 和java中的for语句相同

``` javascript
for (var i = 0; i < <<num>>; i++) {
    ...
}
```

### for in循环语句

- 遍历指定数组或对象中的属性
- 和java中的for each语句类似
- 遍历数组时会跳过为定义的值，所以不适合遍历数组，主要用于遍历对象

``` javascript
for (var o in obj) {
    ...
}
```

### for of循环语句

- 遍历指定数组或对象中的属性
- 和java中的for each语句类似
- ES6新特性

``` javascript
for (var o of obj) {
    ...
}
```

### for each循环语句

- 遍历指定数组或对象中的属性
- 和java中的for each语句类似

``` javascript
obj.forEach(function(o){
    ...
});
```

## 浏览器对象模型（Bower Object Model）

### 定时器

- 时间单位为毫秒

- 示例：在1秒后执行匿名函数

``` javascript
let timer = setTimeout(function(){}, 1000);
```

#### 清除定时器

``` javascript
clearTimeout(timer);
```

### 计时器

- 时间单位为毫秒

- 示例：每隔1秒执行一次匿名函数

``` javascript
let timer = setInterval(function(){}, 1000);
```

#### 取消计时器

``` javascript
clearInterval(timer);
```

### 页面

#### 弹出页面

> `URL`：链接
> `name`：窗口名
> `features`：窗口参数
> `features`：true为替换当前页面，false为新窗口打开。默认为false

``` javascript
let w = window.open(URL,name,features,features);
```

#### 关闭页面

``` javascript
w.window.close();
```

####向页面写入数据

``` javascript
w.window.write(数据);
```

## 文档对象模型（Document Object Model）

- DOM: Document Object Model，文档对象模型，其实就是JS专门为访问html元素提供的一套API。

### 获取元素

- `document`是一个js对象，用于表示当前html网页。当浏览器加载完整个html网页后，会用document对象表示整个html网页

#### 获取当前文档中的body元素

``` javascript
document.body
```

####  获取当前元素的父元素

``` javascript
element.parentNode
```

#### 获取当前元素的所有html内容

``` javascript
element.innerHTML
```

#### 获取特定元素

##### 通过id获取元素

- 返回指定id的元素对象

``` javascript
document.getElementById("");
```

##### 通过class获取元素

- 返回指定class的元素对象数组

``` javascript
document.getElementByClass("")[0];
```

##### 通过标签名获取元素

- 返回指定标签名的元素对象数组

``` javascript
document.getElementsByTagName("")[0];
```

#### 以query格式获取元素

##### 通过id获取元素

``` javascript
document.querySelector("#a");
```

##### 通过class获取元素

``` javascript
document.querySelector(".a");
```

##### 通过标签名获取元素

``` javascript
document.querySelector("div");
```

### 设置标签的内容

``` javascript
var d = document.createElement("div");
d.innerHTML = "文字内容";
```

### 获取父元素

``` javascript
var d = document.getElementById("d");
var parent = d.parentNode;
```

### 获取表示当前时间的字符串

``` javascript
var d = new Date().toLocaleString();
```

### 修改CSS样式

``` javascript
var link = document.getElementById("link");
link.href = "css/*.css";
```

### 节点操作

- 增删改元素

#### 增

``` javascript
//1.创建一个新的div元素
var d = document.createElement("div");
d.innerHTML = "新创建的div";
//2.获取body元素
var b = document.body;
//3.通过父元素(body元素)添加子元素(div元素)
b.appendChild(d);
```

#### 删

``` javascript
//1.获取要删除的元素(id为d)
var d = document.getElementById("d");
//2.获取id为d的元素的父元素
var parent = d.parentNode;
//3.通过父元素删除子元素
parent.removeChild(d);
```

#### 改

``` javascript
//1.获取id为d的元素
var d = document.getElementById("d");
//2.修改元素内容
d.innerHTML = "修改后的文字";
```

## 弹窗

### 弹窗接收字符串

``` javascript
var str = prompt();
```

#### 提示文字

> `<<text>>`：提示文字

``` javascript
var str = prompt(<<text>>);
```

### 弹窗接收布尔值

``` javascript
var str = confirm(<<text>>);
```

## 事件

### 鼠标点击时间

#### html

``` html
<input type="text" onClick="">
```

#### javascript

``` javascript
document.getElementById().onClick = function() {};
```

### 鼠标获取焦点事件

#### html

``` html
<input type="text" onFocus="">
```

#### javascript

``` javascript
document.getElementById().onFocus = function() {};
```

### 鼠标移出焦点事件

#### html

``` html
<input type="text" onBlur="">
```

#### javascript

``` javascript
document.getElementById().onBlur = function() {};
```

### 键盘按下事件

- 获取按下的按键对应的数值

``` javascript
document.getElementById().onkeydown = function(event) {
    console.log(event.keyCode);
};
```

### 鼠标移入事件

``` javascript
document.getElementById().onmouseover = function() {};
```

### 鼠标移出事件

``` javascript
document.getElementById().onmouseout = function() {};
```

## 模版字符串

- ES6新标准
- 使用模版字符串代替字符串拼接

- 原字符串拼接

``` javascript
"name="+name.value;
```

- 新模版字符串

``` javaascript
`name=${name.value}`;
```

## 继承

- 通过原型对象实现继承关系
- 所有子对象会共享原型对象的值

### 定义一个构造函数

``` javascript
let point = function(x,y) {
    this.x = x;
    this.y = y;
}
```

### 通过构造函数创建对象

``` javascript
let p1 = new point(10,20);
let p2 = new point(10,20);
```

### 在原型对象中添加值

``` javascipt
point.prototype.color = "red";
```

### 在子对象修改原型对象中的值

``` javascript
p1.__proto__.color = "black";
```

### 在子对象查看原型对象中的值

``` javascript
p2.__proto__.color;
```

## 更多

[W3school](https://www.w3school.com.cn/jsref/index.asp)

## 参考文献

[知乎——知乎用户](https://www.zhihu.com/question/52662013)
[MDN web docs](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in)
[W3school](https://www.w3school.com.cn/jsref/met_win_open.asp)
[segmentfault——Jason](https://segmentfault.com/a/1190000023719797)

