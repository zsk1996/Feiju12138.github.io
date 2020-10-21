---
title: 【代码】MD5加密
categories:
  - Java
date: 2020-05-27 12:22:57
---

## 前言

Java实现MD5加密字符串

<!-- more -->

## MD5加密

> `<pwd>`：要转换的字符串

``` java
package io.github.feiju12138

import java.math.BigInteger;
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

public class CodeUtil {

    public static void main(String[] args) {
    
        //创建加密计算器
        MessageDigest md5 = null;
        try {
            md5 = MessageDigest.getInstance("MD5");
        } catch (NoSuchAlgorithmException e) {
            e.printStackTrace();
        }

        //加密
        md5.update("<pwd>".getBytes());

        //转换输出
        System.out.println(new BigInteger(1, md5.digest()).toString(16));
    
    }

}
```

## MD5盐值加密

### 使用Spring中的工具类

``` java
import org.springframework.util.DigestUtils;

import java.util.UUID;

public class CodeUtil {

    public static void main(String[] args) {

        // 产生随机字符串，让此字符串作为一个加密盐
        String salt = UUID.randomUUID().toString();

        // 将加盐后的密码进行MD5加密并转换为16进制
        String password = DigestUtils.md5DigestAsHex(("<pwd>"+salt).getBytes());

    }

}
```

### 使用Shiro中的工具类

``` java
import org.apache.shiro.crypto.hash.SimpleHash;

import java.util.UUID;

public class CodeUtil {

    public static void main(String[] args) {

        // 产生随机字符串，让此字符串作为一个加密盐
        String salt = UUID.randomUUID().toString();

        // 将加盐后的密码进行MD5加密1次并转换为16进制
        SimpleHash simpleHash = new SimpleHash("MD5", "<pwd>", salt, 1);
        String password = simpleHash.toHex();

    }

}
```

## 完成 

