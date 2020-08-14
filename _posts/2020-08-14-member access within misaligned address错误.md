---
layout: post
title: "member access within misaligned address 错误"
date: 2020-08-14 15:22:07
description:奇怪啊
tags:
 - C++探究
 - 错误研究
---

### 问题说明

leetcode错误提示：member access within misaligned address 0xbebebebebebeb for type 'struct ***'

### 原因

结构体或类内的指针类成员没有分配初值。
