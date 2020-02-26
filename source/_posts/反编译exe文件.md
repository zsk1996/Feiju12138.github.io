---
title: 【笔记】反编译 exe 文件
categories:
  - MacOS
date: 2020-02-18 23:58:15
---

## 前言

将`.exe`文件反编译为`.py`文件

<!-- more -->

## 克隆 pyinstxtractor

``` sh
git clone https://github.com/countercept/python-exe-unpacker.git 
```

## 将exe文件转换为pyc文件

> `<file_name>`：文件名

``` sh
cd python-exe-unpacker
python pyinstxtractor.py <file>.exe
```

## 添加magic和时间戳

- 为`lockyfud.pyc`文件头添加4字节的`magic`和4子节的`时间戳`

- 在`struct`文件头复制4字节作为`lockyfud.pyc`文件的`magic`

- 4字节的时间戳设置为`00 00 00 00`

## 将pyc文件转换为py文件

### 安装uncompyle6

``` sh
pip install uncompyle6
```

### 将pyc文件转换为py文件

``` sh
uncompyle6 <file_name>.pyc > lock.py
```

## 参考文献

[CSDN——G4rb3n](https://blog.csdn.net/m0_37552052/article/details/88093427)

