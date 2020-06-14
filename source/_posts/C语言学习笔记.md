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

## 输入字符

``` c
char inputChar = getchar();
```

## 格式化输入

- `&`用于取数据的内存地址

``` c
char dist;
scanf("%c", &dist);
```

### 输入字符串

- 输入字符串不需要`&`，因为字符数组本身就为内存地址

``` c
char buf[10];
scanf("%c", buf);
```

## 数组

- 数组下标从0开始
- C语言的数组创建的时候，其实是直接使用的其他被遗弃的内存空间，所以默认会有数值且不确定，使用之前可以进行清零操作

### 创建时仅初始化

> `<num>`：数组长度

``` c
<type> <name>[<num>];
```

### 创建时添加数据

> `<value_1>`：值

``` c
<type> <name>[] = {<value_1>, <value_2>, ...};
```

## 二维数组

### 创建时仅初始化

``` c
<type> <name>[<num>][<num>];
```

### 创建时添加数据

``` c
<type> <name>[<num>][<<num>>] = {{<value_1>, <value_2>}, {<value_3>, <value_4>}}
```

## 字符数组

### 引入头文件

``` c
#include <string.h>
```

### 字符串长度

``` c
char str[<num>];
strlen(str);
```

### 字符串初始化

> `<string>`：字符串
> `<char_1>`、`<char_2>`：字符

> `'\0'`：字符串结尾字符

``` c
char str[<num>] = "<string>";
char * str = "<string>";
char str[<num>] = {'<char_1>', '<char_2>', '\0'}
```

### 清零字符串

> `<num>`：格式化后的数字，值为`0`时为清零操作
> `<len>`：格式化的长度，通常为字符串长度

``` c
memset(<string>, <num>, <len>);
```

## 连接字符串

### 引入头文件

``` c
#include <string.h>
```

### 完整连接

``` c
// 定义一个字符串作为缓冲区
char str[10];

// 清零字符串
memset(str, 0, 10);

// 定义两个需要连接的字符串
char * str1 = "Hello";
char * str2 = "World";

// 连接字符串
strcat(str, str1);
strcat(str, str2);
```

### 片段连接

> `<num>`：指明需要连接的长度

``` c
strncat(str, str1, <num>);
```

## 格式化字符串

- 将多个其他类型的数据转化为字符串

``` c
char * str = "s";
int num = 100;

// 定义一个字符串作为缓冲区
char dist[10];

// 初始化字符串
memset(dist, 0, 10);

// 合并为一个字符串
sprintf(dist, "%s%d", str, num);
```

### 反向格式化

``` c
char * str = "m100";
char buf[10];
int num;

memset(buf, 0, 10);

sscanf(str, "%1s%d", buf, &num);
```

## 字符串转换为其他类型

> `<str>`：需要转换的字符串

|转化之前的类型|使用到的函数|
|---|---|
|转化为浮点类型|`atof(<str>);`|
|转化为int类型|`atoi(<str>);`|
|转化为long int类型|`atol(<str>);`|
|转化为long long int类型|`atoll(<str>);`|

## 字符串比较

- 如果直接用`==`做比较，实际上是比较存储字符串的内存地址
- `strcmp`函数会返回两个字符串的“计算结果”，结果为0则相等，结果不为0则不相等

``` c
int result = strcmp(<str_1>, <str_2>);
```

## 字符串截取

- 区分大小写
- 如果搜索不到，就返回`(null)`

### 通过比较截取

#### 从前往后搜索

- 从第一次出现指定字符的位置截取字符串到结尾

``` c
char * strNew = strchr("Hello World", 'o');
```

#### 从后往前搜索

-  从最后一次出现指定字符的位置截取字符串到结尾

``` c
char * str = strrchr("Hello World", 'o');
```

#### 搜索字符串

- 从第一次出现指定字符串的位置截取字符串到结尾

``` c
char * str = strstr("Hello World", "Wo");
```

### 通过位置截取

#### 指定结束位置

- 从开始位置截取到指定位置

> `<num>`：截取截止位置，字符串下标从1开始

``` c
char str[10];
strncpy(str, "Hello World", <num>);
```

### 通过指针截取

- 将指针向后增加，直接截取指针位置到结尾的字符串

> `<num>`：截取起始位置

``` c
char * str = "Hello World"
char * strNew = str + <num>;
```

### 通过指针和位置共同截取

- 为了从指定位置截取到指定位置，可以先使用`通过指针截取`指定截取起始位置，再用`通过位置截取`指定截取截止位置

> `<num_1>`：截取起始位置
> `<num_2>`：截取截止位置

``` c
char * str = "Hello World";
char * str1 = str + <num_1>;
char str2[10];
strncpy(str2, str1, <num_2>);
```

## 函数

### 定义函数

> `<fun_name>`：函数名

``` c
void <fun_name>() {
    ...
}
```

#### 调用函数

``` c
void main(void) {
    <fun_name>();
}
```

### 定义有参数传入的函数

> `<para_type>`：参数类型
> `<para_name>`：参数名

``` c
void <fun_name>(<para_type> <para_name>) {
    ...
}
```

#### 调用函数

> `<para_value>`：对应类型的值

``` c
void main(void) {
    <fun_name>(<para_value>);
}
```

#### 传入多个参数

``` c
void <fun_name>(<para_type_1> <para_name_1>, <para_type_2> <para_name_2>) {
    ...
}
```

### 定义有返回值的函数

> `<type>`：返回值类型

``` c
<type> <fun_name>() {
    ...
}
```

#### 调用函数

> `<name>`：变量名

``` c
void main(void) {
    <type> <name> = <fun_name>();
}
```

### 关于main函数

#### main函数的参数

- 在命令行执行程序时，main函数传入了两个参数，这两个函数分别是`执行程序传入的参数数量`和`执行程序传入的参数值`

``` c
int main(int argc, char ** argv) {
    ...
    return EXIT_SUCCESS
}
```

- 执行C语言程序

> `<name>`：文件名

``` sh
./<name>
```

- 事实上，执行这个程序时，默认会传入`1`和`./<name>`参数

#### main函数的返回值

- main函数返回值类型为int类型
- 当返回为`0`时，表示程序正常退出
- 当返回其他值，表示程序异常退出

### 定义有可变参数传入的函数

#### 头文件

``` c
#include <stdarg.h>
```

#### 定义函数

``` c
int sum(int n, ...) {
    ...
}
```

#### 开始可变参数的获取

``` c
va_list args;
va_start(args, n);
```

#### 遍历每个值

``` c
for(int i = 0; i < n; i++) {
    int arg = va_arg(args, int);
}
```

#### 结束可变参数的获取

``` c
va_end(args);
```

### 定义私有的函数 

``` c
static void main() {
    ...
}
```

## 预设常量

- 通过编译器传常量

> `<name>`：文件名
> `<value>`：常量名和常量值

``` sh
gcc <name>.c -D<value>
```

## 平台判断

``` c
#define WIN 1
#define LINUX 2
#define MAC 3

void main() {

#if PLATFORM==WIN
    ...
#elif PLATFORM==LINUX
    ...
#elif PLATFORM==MAC
    ...
#else
    ...
#endif

}
```

## 防止头文件重复引用

> `<name>`：此`.h`文件名

``` c
#ifndef <name>_H_
#define <name>_H_

#endif
```

### 新型方式

``` c
#pragma once
```

## 宏函数

- 宏函数内不用写类型
- 结尾不用写";"
- 换行需要在本行行末写"\"

### 定义一个宏函数

- 定义一个判断大小的宏函数

``` c
#define MAX(A, B) A>B?A:B
```

### 多行宏函数

- 定义一个循环执行代码的函数

``` c
#define LOOP(FROM, TO, CONTENT)\
    for(int i = FORM; i < TO; i++) {\
        CONTENT\
    }
```

#### 执行宏函数

- 循环10次执行输出下标代码

``` c
LOOP(0, 10, printf("Index is %d\n", i););
```

### 宏函数参数连接

``` c
void jikexueyuanSayHello() {
    ...
}

#define calljkxy(NAME) jikexueyuan##NAME()

int main(void) {
    
    calljkxy(SayHello);
    
    return EXIT_SUCCESS;

}
```



## 未完待更

## 参考文献

[哔哩哔哩——C3程序猿](https://www.bilibili.com/video/av29473098)
[哔哩哔哩——HACK学习](https://www.bilibili.com/video/BV1ds411T7bj)

