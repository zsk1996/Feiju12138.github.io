---
title: 【笔记】Maven 配置代理
categories:
  - Java
date: 2019-12-29 11:36:41
---

## 前言

`Maven`官方源在国外，所以需要配置代理获取

<!-- more -->

## 配置代理

- 编辑`Maven`配置文件

``` sh
vim /usr/local/Cellar/maven/3.6.3_1/libexec/conf/settings.xml
```

- 修改`<proxies></proxies>`中的配置

> `<id>`：自定义id
> `<active>`：激活状态
> `<protocol>`：代理协议
> `<username>`：代理用户名认证（不需要认证可不填）
> `<password>`：代理密码认证（不需要认证可不填）
> `<host>`：代理的IP地址
> `<port>`：代理的端口号
> `<nonProxyHost>`：不需要代理的主机（可不填）

``` xml
<proxies>
    <proxy>
        <id>optional</id>
        <active>true</active>
        <protocol>http</protocol>
        <username>proxyuser</username>
        <password>proxypass</password>
        <host>proxy.host.net</host>
        <port>80</port>
        <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
    <proxy>
</proxies>
```

## 完成

## 参考文献

[博客园——Memory4Young](https://www.cnblogs.com/memory4young/p/maven-http-proxy-setting.html)

