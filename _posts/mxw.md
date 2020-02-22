---
layout: post
title: "二分法探究"
date: 2020-01-27 14:48:51
description: 二分插入和二分搜索的一些探究
tags: 
 - algorithm
 - 二分法
---

#### 二分法

#### 常见函数

#### 二分插入的位置探究

> 究竟应该返回谁？

```
class Solution {
public:
    int mySqrt(int x) {
        int left = 1;
        int right = x/2 + 1;
        int mid;
        while (left <= right) {
            mid = (left + right + 1)/2;
            if(mid * mid > x)
                right = mid - 1;
            else if(mid * mid < x)
                left = mid + 1;
            else
                return mid;
        }
        return right;
    }
};
```

<https://leetcode-cn.com/explore/learn/card/binary-search/>



<https://leetcode-cn.com/problems/find-peak-element/submissions/>