---
layout: post
title: "论文笔记(1)——利用不确定性估计提升Back-Translation的质量"
date: 2019-11-12 02:30:19
description: Improving Back-Translation with Uncertainty-based Confidence Estimation
tags: 
 - Machine Translation
 - NLP
 - 论文笔记
---



#### 论文信息

题名: Improving Back-Translation with Uncertainty-based Confidence Estimation

来源: EMNLP2019

年份: 2019

学习原因: 组会

<br>

#### 摘要

在NMT中，back-translation技术一直是一种简单并且有效的提高稀缺资源翻译的技术。然而，通过back-translation生成的双语语料往往噪声很大。在这篇文章中，作者提出了基于不确定度的词级别和句子级别的置信度评估方法，利用评估的好坏提高Back-Translation的质量。并对中-英和英-德的翻译任务进行实验，实验证明通过进行不确定性评估，反向翻译表现会极大提升。



