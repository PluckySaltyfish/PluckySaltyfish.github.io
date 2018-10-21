---
layout: post
title: "NLP with Python观察笔记(1)"
date: 2018-09-25 02:47:56
description: 1.1 nltk的一些简单的函数
tags: 
 - NLP
---

### nltk.text.Text的方法

##### 查找上下文

`.concordance(word, width=79, lines=25)`在text中查找和word一致的句子，显示其上下文，不区分大小写。

`.similar(word, num=20)`在text中查找上下文与word相同的词。

`.common_contexts(word, num=20)`在text中查找word的上下文（按出现频率由高到低排序），当word为列表时，列出列表中词相同的上下文。

![img]({{ site.baseurl | prepend:site.url}}/images/image-20180925114504608.png){: .center-image }

#### 离散图

`.dispersion_plot(word) `显示指定word的离散词频，横轴代表整篇文章，一道竖线代表出现一次。

![img]({{ site.baseurl | prepend:site.url}}/images/dispersion.png){: .center-image }