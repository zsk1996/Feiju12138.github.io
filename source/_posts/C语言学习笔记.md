---
title: 【笔记】C语言学习笔记
categories:
  - C/C++
date: 2020-03-04 16:14:46
---

## 前言

C是一种通用的编程语言，广泛用于系统软件与应用软件的开发。于1969年至1973年间，为了移植与开发UNIX操作系统，由丹尼斯·里奇与肯·汤普逊，以B语言为基础，在贝尔实验室设计、开发出来。 C语言具有高效、灵活、功能丰富、表达力强和较高的可移植性等特点，在程序设计中备受青睐，成为最近25年使用最为广泛的编程语言。（[维基百科](https://wiki.hk.wjbk.site/zh-hans/C语言)）

<!-- more -->

## 注释

### 单行注释

- `//`后的文字均为单行注视

### 多行注释

- `/* code */`

## 头文件

- 导入C/C++语言函数库

``` c
#include <stdio.h>
#include <stdlib.h>
```

## 主函数

- 应用程序入口，操作系统调用程序的接口
- 一个项目只能有一个main函数

### 常见的五种主函数

#### C语言标准主函数形式

- void表示不接收任何参数
- 无void表示参数类型和数量不确定

``` c
int main(void)
{
    return 0;
}
```

#### C/C++标准主函数形式，使用命令行参数

``` c
int main(int argc, char* argv[])
{
    return 0;
}
```

#### C++标准主函数形式

``` c
int main()
{
    return 0;
}
```

#### 老版本

- 老标准支持的写法，现在的C语言还支持这种写法，但尽量不要这么写
- C++不支持这种写法

``` c
main()
{}
```

#### 不提倡

- C++之父说，这种形式的主函数，在C/C++语言中都没有被定义
- 书上说，这种主函数写法逻辑上符合，而且有很多系统支持，但是考虑到代码的移植性，建议用标准型式，标准型式所有系统都支持

``` c
void main()
{}
```

## 变量和常量

### 变量

> `<type>`：数据类型
> `<name>`：数据名
> `<value>`：数据值

``` c
<type> <name> = <value>;
```

### 常量

- 常量名全部大写，多个单词用`_`隔开

#### 方法一

``` c
#define <name> <value>
```

#### 方法二

``` c
const <type> <name> <value>
```

## 数据类型

### 无符号数据类型

``` c
unsigned <type> <name> = <value>;
```

### 整型

``` c
int <name> = <value>;
```

#### 其他进制数据

##### 2进制数据

- 以`0b`开头

##### 8进制数据

- 以`0`开头

##### 16进制数据

- 以`0x`开头

#### 不同系统下的相同数据

- 以`<num>_t`结尾为特定位平台数据
- 以`u_`开头为无符号数据

##### 8位系统

``` c
int8_t <name> = <value>;
u_int8_t <name> = <value>;
```

##### 16位系统

``` c
int16_t <name> = <value>;
u_int16_t <name> = <value>;
```

##### 32位系统

``` c
int32_t <name> = <value>;
u_int32_t <name> = <value>;
```

##### 64位系统

``` c
int64_t <name> = <value>;
u_int64_t <name> = <value>;
```

#### 长整型

- 32位系统，占4字节
- 64位系统，占8字节

``` c
long <name> = <value>;
```

- 无论32位系统还是64位系统，都占8字节

``` c
long long <name> = <value>;
```

### 实数类型

#### 单精度

- 4字节，32位

``` c
float <name> = <value>;
```

#### 双精度

- 8字节，64位

``` c
double <name> = <value>;
```

#### 长双精度

- 16字节，128位

``` c
long double <name> = <value>;
```

### 字符型

#### 字符常量

##### 换行符

- `\n`

##### 回车符

- `\r`

##### 退格符

- `\b`，相当于`back space`

##### 制表符

- `\t`

##### 换页符

- `\f`

##### 其他转义字符

|转义前|转义后|
|---|---|
|\|\\|
|"|\"|
|'|\'|

#### 字符变量

##### 字符

- 用单引号引起来

### 自定义类型

#### 为数据类型起别名

> `<type_old>`：起名前
> `<type_new>`：起名后

``` c
typedef <type_old> <type_new>
```

## if语句

> `<boolean>`：布尔值

``` c
if (<boolean>) {
    ...
}
```

``` c
if (<boolean>) {
    ...
} else {
    ...
}
```

``` c
if (<boolean>) {
    ...
} else if (<boolean>) {
    ...
}
```

## switch语句

> `<name>`：变量名
> `<value_1>`：第一种值
> `<value_2>`：第二种值

``` c
switch (<name>) {
    case <value_1>:
        ...
        break;
    case <value_2>:
        ...
        break;
    default:
        ...
}
```

## goto语句

- 到达goto语句时，执行跳转到指定的标签

> `<label>`：标签

``` c
<label>:
...

goto <label>
```

## for循环

``` c
for (int i = 0; i < 10; i ++) {
    ...
}
```

### break语句

- 跳出循环

### continue语句

- 终止本次循环

### 嵌套循环

- 九九乘法表小案例

``` c
for (int i = 1; i <= 9; i ++) {
    for (int j = 1; j <= i; j ++) {
        printf("%d * %d = %d \t", i, j, i*j);
    }
    printf("\n");
}
```

## while循环

``` c
while (<boolean>) {
    ...
}
```

``` c
do {
    ...
} while (<boolean>);
```

## 输出字符和字符串

### 输出字符

> `<num>`：0~255的int数，或一个字符

``` c
putchar(<num>);
```

### 输出字符串

> `<string>`：字符串，或一个字符数组

``` c
puts(<string>);
```

## 格式化输出

|输出前|输出后|
|---|---|
|%d|整形|
|%03d|在`%`后加`<num_1><num_2>`，表示在改值不足`<num_2>`位数前补`<num_1>`，如果`<num_1>`为空，则在数前补空格|
|%u|无符号整数|
|&o|8进制数|
|%x|16进制数（英文小写）|
|%X|16进制数（英文大写）|
|%f|浮点数（双精度）|
|%.2f|在`%`后加`.<num>`，表示保留小数点后`<num>`个有效数字|
|%c|字符|
|%s|字符串|
|%ld|长整型|
|%Lf|长浮点数（双精度）|
|%p|指针|



## 未完待更

## 参考文献

[哔哩哔哩——C3程序猿](https://www.bilibili.com/video/av29473098)
[哔哩哔哩——HACK学习](https://www.bilibili.com/video/BV1ds411T7bj)

