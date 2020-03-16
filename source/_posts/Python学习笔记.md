---
title: 【笔记】Python 学习笔记
categories:
  - Python
date: 2020-02-07 14:29:09
---

## 前言

由于笔记不详细，强烈建议在已掌握其他编程语言的情况下学习本笔记内容

<!-- more -->

## 安装 python

### Windows

- 在官网下载

`https://www.python.org`

### Linux

- 系统预装

### MacOS

1. 系统预装`2.x`版本

2. 使用`brew`安装

``` sh
brew search python
```

3. 使用`pyenv`安装并管理多个`python`版本

[传送门](https://feiju12138.github.io/2020/02/06/Pyenv学习笔记/)

## python 运行方式

### 通过交互式解释器

``` sh
python
```

#### 退出

``` sh
>>> exit()
```

### 以文件的方式运行

> `<file_name>`：`python`文件名

#### 创建 python 文件

``` sh
touch <file_name>.py
```

#### 提升执行权限

``` sh
chmod +x <file_name>.py
```

#### 编辑 python 文件

``` sh
vim <file_name>.py
```

#### 添加 python 文件头

- 文件头指定解释器

``` python
#!/usr/bin/python
```

##### 自动查找解释器

``` python
#!/usr/bin/env python
```

#### 使用 python命令 执行 python文件

``` sh
python <file_name>.py
```

#### 直接执行 python文件

``` sh
./<file_name>.py
```

## 支持 tab 补齐的交互解释器

### 导入模块方式

- 只能本次使用

``` sh
>>> import readline
>>> import rlcompleter
>>> readline.parse_and_bind("tab:complete")
```

### 使用环境变量方式

- 可以一直使用

#### 创建一个脚本

``` sh
touch tab.py
```

#### 编辑脚本

``` sh
vim tab.py
```

#### 把代码写入文件

``` python
#!/usr/bin/env python

import readline
import rlcompleter
readline.parse_and_bind("tab:complete")
```

#### 提升可执行权限

``` sh
chmod a+x tab.py
```

#### 刷新环境变量

``` sh
source ~/.bash_profile
```

## 安装 pip

- `python 2.7`默认安装`pip`

### MacOS

- 使用`pyenv`安装的`python`自带`pip`
- 使用`pyenv`配置好`python`的默认版本，就可以直接使用`pip`命令

## 语句块缩进

- python代码块通过缩进对齐表达代码逻辑而不是使用大括号
- 缩进表达一个语句属于哪个代码块
- 缩进通常使用4个空格

## 基本 python 语句

### 输出语句

> `<value>`：输出的值

``` python
print(<value>)
print(<value>, <value>)
print(<value> + <value>)
```

### 输入语句

``` python
input()
```

#### 有提示的输入语句

> `<value>`：提示语句

``` python
input("<value>")
```

#### 把输入的语句赋值给变量

> `<name>`：变量名

``` python
<name> = input("<value>")
```

### 查看数据类型

> `<value>`：数据

``` python
type(<value>)
```

### 类型转换

- `str`类型转为`int`类型

> `<str>`：str类型数据

``` python
int(<str>)
```

- `int`类型转为`str`类型

> `<int>`：int类型数据

``` python
str(<int>)
```

## 注释

### 单行注释

- 从`#`开始，直到一行结束的内容都是注释

### 文档字符串

#### 创建文档

> `<name>`：文档名

``` sh
touch <name>.py
```

#### 编辑文档

> `<NAME>`：用于注释文件名称
> `<DESCRIPTION>`：用于注释文档描述
> `<FUCTIONS>`：用于注释函数描述

``` python
"""<NAME>

<DESCRIPTION>
"""

def fuction():
    "<FUCTIONS>"
    print("end")
```

#### 查看文档帮助

``` python
import <name>
help(function)
```

## 变量定义

### 变量定义规则

- 第一个字符只能是`字母`或`下划线`（不建议使用下划线）
- 后续字符只能是`字母`、`数字`、`下划线`
- 区分大小写

### 命名习惯

- 有意义
- 简短
- 全部采用小写字母
- 多个单词之间用下划线隔开
- 变量一般使用名词，函数使用谓词（动词+名词）
- 类名首字母大写，使用驼峰原则

## 变量赋值及运算

### 变量赋值

- 使用`=`为变量赋值

- python变量首次使用不需要声明变量类型，但必须初始化，初始化时将定义变量类型

### 变量运算

#### 标准运算符

- `+`、`-`、`*`、`/`、`//`、`%`、`**`

> `/`：除号表示除法运算，`整型`与`整型`运算结果数据类型为`整型`，`整型`与`浮型`运算结果数据类型为`浮点型`
> `//`：`地板除`表示整除运算。结果为`保留小数的结果`产生的`两个相近似整数`的`较小的一个整数`，结果数据类型根据`被除数`决定是`整数型`还是`浮点型`
> `%`：求模运算，结果为两数相除的余数
> `**`：幂运算，结果为两数的乘方

- python还支持`+=`、`-=`、`*=`、`/=`
- 但python不支持`++`和`--`操作，`++`和`--`放在变量前表示两次正负号运算操作，放在变量后会报错

#### 比较运算符

- `<`、`<=`、`>`、`>=`、`==`、`!=`、`<>`

> `!=`和`<>`均为不等号，但常用`!=`表示不等号

##### 连续比较

- python支持连续比较

- `A < B > C`等价于`A < B and B > C`

#### 逻辑运算符

- 根据优先级排列分别是：`not`、`and`、`or`

- 结果为`True`或`False`（首字母大写）

## 数据类型

### 数字类型

> `int`：整型
> `long`：长整型
> `bool`：布尔值，值为`True`和`False`，分别对应`1`和`0`
> `float`：浮点型

> `complex`：复数，通常只作数学运算使用

#### 进制表示

- python默认以`10进制数`显示
- 数字以`0`开头表示`8进制数`
- 数字以`0x`或`0X`开头表示`16进制数`
- 数字以`0b`或`0B`开头表示`2进制数`

### 字符串

- 引号之间的字符集合组成字符串（`''`或`""`都可以）

- 一对三个（单或双）引号的组合之间的字符集合组成`可以保留格式`的字符串

- python不区分字符和字符串

#### 字符串切片

``` python
str = "python"
```

##### 正序编号

- 字符串第一个字符下标为`0`
- 表示为：`str[0]`
- 结果为：`p`

##### 倒序编号

- 字符串最后一个字符下标为`-1`
- 表示为：`str[-1]`
- 结果为：`n`

##### 区间编号

###### 闭区间

- 第一个字符到第二个字符下标区间为`[0,1]`
- 表示为：`str[0:1]`
- 结果为：`py`

###### 开区间

- 从头开始到第二个字符下标区间为`[0,1]`
- 表示为：`str[:1]`
- 结果为：`py`

###### 根据步长取值

- 从下标为`1`的字符开始，步长为`2`
- 表示为：`str[1::2]`
- 结果为：`yhn`

#### 字符串拼接

- 使用`+`相连的多个字符串，拼接为一个字符串

##### 按倍数拼接

- 使用`*`指定拼接次数，拼接为一个字符串

#### 字符串长度

> `<string>`：字符串

``` python
<string>.len()
```

#### 字符串查找

##### 判断是否存在

> `<string>`：原字符串
> `<value>`：查找的关键字

``` python
<value> in <string>
```

##### 判断是否不存在

``` python
<value> not in <string>
```

### 列表

- 列表是存放多个数据的集合，数据类型可以为任意类型
- 列表用`[]`定义，用`,`隔开多个数据
- 列表也可以使用下标切片
- 列表可以包含列表，子列表切片用`[][]`取出数据
- 列表数据可以修改

#### 追加数据

- 在列表末尾追加数据

> `<list>`：列表名
> `<value>`：追加的数据

``` python
<list>.append(<value>)
```

### 元组

- 元组类似于列表，用`()`定义
- 元组数据不可以修改

### 字典

- 字典是由键值对（key-value）构成的映射数据类型，用`{}`定义
- 字典不是顺序类型，不支持下标操作

#### 查看字典长度

> `<dict>`：字典

``` python
<dict>.len()
```

#### 字典查找

- 字典只能查找`键`

> `<key>`：键值对的键

``` python
<key> in <dict>
```

##### 通过键查找值

``` python
<dict>[<key>]
```

#### 添加或修改键值对

- 如果`<key>`：存在，则为修改键值对，如果`<key>`：不存在，则为修改键值对

``` python
<dict>[<key>] = <value>
```

### 数据类型的总结

#### 数据类型的分类

##### 按存储模型分类

###### 标量类型

- 数值、字符串

###### 容器类型

- 列表、元组、字典

##### 按更新模型分类

###### 可更新类型

- 列表、字典

###### 不可更新类型

- 数字、字符串、元组

##### 按访问模型分类

###### 直接访问

- 数字

###### 顺序访问

- 字符串、列表、元组

###### 映射访问

- 字典

## 判断语句

### 语法

> `<expression>`：布尔表达式或布尔值
> `<suite>`：代码块

``` python
if <expression>:
    <suite>
else:
    <suite>
```

#### 特殊布尔值

- 非零数字、非空对象值为`True`
- `None`、数字零、空对象（空字符串、空列表、空元组、空字典）值为`False`

#### 多分支

##### 语法

``` python
if <expression>:
    <suite>
elif <expression>:
    <suite>
else:
    <suite>
```

- python没有`switch case`这样的替代品

## while 循环

### 语法结构

``` python
while <expression>
    <suite>
```

#### break 语句

- 跳出循环

``` python
while <expression>
    <suite>
    break
```

#### continue 语句

- 退出当前循环

``` python
while <expression>:
    <suite>
    continue
```

#### else 语句

- else子句只在循环完成后执行
- break语句也跳过else块

``` python
while <expression>:
    <suite>
else:
    <suite>
```

## for 循环

### 语法结构 

> `<var>`：变量
> `<string>`：任何可切片数据

- 重复`len(<string>)`次循环，按从头到尾顺序，每次循环取出一个切片，赋值给变量`<var>`

``` python
for <var> in <string>
    <suite>
```

- for循环也支持`break`、`continue`、`else`语句

#### range 函数

- `range函数配合`的语句，组成可以实现`指定循环次数`的for循环语句

> `<start>`：表示开始值，默认值为`0`
> `<end>`：表示结束值
> `<step>`：表示步长值，默认值为`1`

- 从`开始值`开始循环，每次增加`步长值`，增加到`结束值`结束跳出结束循环（不包含）

``` python
for <var> in range():
    <suite>
```

> 参数列表
>> 一个参数：`range(<end>)`
>> 两个参数：`range(<start>, <end>)`
>> 三个参数：`range(<start>, <end>, <step>)`

##### xrange 函数

- `xrange()`类似`range()`，不过当你有一个很大的范围列表时，`xrange()`可能更为适合，因为它不会在内存里创建列表的完整拷贝
- 它只被用在for循环中，在for循环外使用它没有意义
- 它的性能远高出`range()`，因为它不生成整个列表

### 列表解析

- 用来动态创建列表

#### 语法结构

> `<value>`：需要存放到列表的数据
> `<for_in>`：`不含语句块`的for循环
> `<for_range>`：`range函数配合`的`不含语句块`的for循环

``` python
[<value> <for_in>]
[<value> <for_range>]
```

## 参考文献

达内教育

