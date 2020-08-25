---
title: 【破解】Navicat破解
categories:
  - MacOS
date: 2020-08-10 18:18:52
password: pojie
---

## 前言

使用`navicat-keygen`破解Mac版Navigate 15

<!-- more -->

## 准备工作

- [Navicat 15.0.8](http://download.navicat.com.cn/download/navicat150_premium_cs.dmg)

## 破解

### 使用navicat-patcher替换掉公钥

``` sh
cd bin
./navicat-patcher /Applications/Navicat\ Premium.app
```

![01.png](/images/20200810181852/01.png)

- 代码执行结束后会在当前目录下生成`RegPrivateKey.pem`文件

### 生成一份自签名的代码证书，并总是信任该证书

- 打开钥匙串访问

- `钥匙串访问`->`证书助理`->`创建证书`

![02.png](/images/20200810181852/02.png)

> `名称`：Navicat
> `身份类型`：自签名根证书
> `证书类型`：代码签名

![03.png](/images/20200810181852/03.png)

- 右键新建好的证书->`显示简介`

- 信任设置全部改为`始终信任`（将第一个选项改为始终信任其他会默认被修改）

![04.png](/images/20200810181852/04.png)

### 用codesign对Navicat Premium.app重签名

- 如果`Navicat Premium`版本号高于`15`，必须先签名`libcc-premium.dylib`，再签名`Navicat Premium.app`

``` sh
codesign -f -s Navicat /Applications/Navicat\ Premium.app/Contents/Frameworks/libcc-premium.dylib
codesign -f -s Navicat /Applications/Navicat\ Premium.app
```

### 使用navicat-keygen来生成 序列号 和 激活码

``` sh
./navicat-keygen ./RegPrivateKey.pem
```

![05.png](/images/20200810181852/05.png)

- 第一个问题回复1（也就是选择Navicat的语言版本）
- 第二个问题直接回车（也就是默认破解15版本）
- 此时程序提供了一个激活码，保留备用
- 第三个问题设置一个用户名（可以自定义）
- 第四个问题设置一个企业名（可以自定义）
- 第五个问题输入公钥（切记此时不要继续回车操作，现在进入下一步操作，不要关闭终端）

### 断网激活

- 断开网络，打开Navicat
- 在左侧激活区域输入刚刚得到的激活码
- 此时一定是激活失败，选择离线激活
- 复制公钥，粘贴到刚刚暂停的终端上，按两次回车确认
- 此时程序会返回一个私钥，将私钥复制并粘贴到Navicat

![06.png](/images/20200810181852/06.png)

## 完成

- 截图纪念

![07.png](/images/20200810181852/07.png)

## 参考文献

[Github——HeQuanX](https://github.com/HeQuanX/navicat-keygen-tools)
[奇爱屋](https://www.7i5.com/1226.html)
