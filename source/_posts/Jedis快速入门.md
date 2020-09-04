---
title: 【代码】Jedis快速入门
categories:
  - Java
date: 2020-08-30 20:05:13
---

## 前言

通过Jedis使用Java代码操作Redis数据库

<!-- more -->

## 代码

``` java
package io.github.feiju12138;

import org.junit.Test;
import redis.clients.jedis.Jedis;

public class JedisTests {

    @Test
    public void testJedis() {
        // 1. 获取连接
        Jedis jedis = new Jedis("localhost", 6379); // 如果连接本机且端口号为默认，可以使用无参构造
        jedis.auth("123456");

        // 2. 操作
        jedis.set("username", "zhangsan");

        // 3. 关闭连接
        jedis.close();
    }

}
```

## 完成

## 参考文献

[哔哩哔哩——黎曼的猜想](https://www.bilibili.com/video/BV1uJ411k7wy)
[CSDN——小道仙](https://blog.csdn.net/Tomwildboar/article/details/89296322)

