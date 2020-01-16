---
layout: post
title: "不同的二叉搜索树"
date: 2019-07-26 15:39:38
description: 排序 面试题
tags: 
 - Algorithm
 - 排序
---

###### 题目描述 

给定一组非负整数，重新排列它们的顺序使之组成一个最大的整数。

[题目链接](https://leetcode-cn.com/problems/largest-number/)



##### 样例输入

    [3,30,34,5,9]



##### 样例输出

    9534330



#### 解题思路

实际上这个是今年OPPO二面的一道口答题，在LeetCode上找到了原题。之前在和鑫神在想逻辑，思路都是怎么在暴力比较的办法里优化，但是却没有想到仅仅通过定义自定义排序规则就可以直接实现，着实感慨。

思路就是对数列进行排序，然后依照顺序直接进行拼接。唯一需要知道的排序条件就是：对于两个数A和B，如果AB>BA，那么A就放在B的前面。

#### 示例代码

```c++
class Solution {
public:
    bool static cmp(string s1,string s2){
        string a = s1 + s2;
        string b = s2 + s1;
        return a > b;
    }
    string largestNumber(vector<int>& nums) {
        int n = nums.size();
        vector<string>s_nums;
        for (int i = 0; i < n; i++) {
            s_nums.push_back(to_string(nums[i]));
        }
        sort(s_nums.begin(), s_nums.end(), cmp);
        if(s_nums[0] == "0")
            return "0";
        string res = "";
        for (int i = 0; i < n; i++) {
            res += s_nums[i];
        }
        return res;
    }
};
```

