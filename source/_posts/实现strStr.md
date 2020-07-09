---
title: 【代码】实现strStr()
categories:
  - LeetCode
date: 2020-07-04 15:16:00
---

## 前言

LeetCode答案，语言Java

<!-- more -->

## 问题

- [https://leetcode-cn.com/problems/implement-strstr/](https://leetcode-cn.com/problems/implement-strstr/)

## 源代码

``` java
import java.util.Arrays;

class Solution {
    public int strStr(String haystack, String needle) {

        for (int i = 0; i < haystack.length()-(needle.length()-1); i++) {
            if (needle.equals(haystack.substring(i, i+needle.length()))) {
                return i;
            }
        }

        return -1;
    }
}
```

## 完成

