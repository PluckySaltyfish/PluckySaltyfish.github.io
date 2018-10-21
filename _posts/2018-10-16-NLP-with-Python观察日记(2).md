---
layout: post
title: "NLP with Python观察笔记(2)"
date: 2018-09-25 02:47:56
description: 1.3-1.4练习答案
tags: 
 - NLP
---

代码中的写法是ntlk3.3。

### 频率分布

> 1:使用 text2 尝试前面的频率分布的例子。注意正确使用括号和 大写字母。

```python
fdist2 = FreqDist(text2)
vocabulary = []
for item in fdist.most_common(50):
    vocabulary.append(item[0])
```

### 细粒度的选择词

> 2:在 Python 解释器中尝试上面的表达式，改变文本和长度条件做 一些实验。如果改变变量名，你的结果会产生什么变化吗?如使用[word for word in vocab if ...] 

 相关Python语法见[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431779637539089fd627094a43a8a7c77e6102e3a811000)

### 词语搭配和双联词

bigrams()是一个生成器，获取值和捕获异常，循环输出见[廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317799226173f45ce40636141b6abc8424e12b5fb27000)

### 条件

> 3:运行下面的例子，尝试解释每一条指令中所发生的事情。然后， 试着自己组合一些条件 

```python
>>> sorted([w for w in set(text7) if '-' in w and 'index' in w])
# 连接词，并且含有index
>>> sorted([wd for wd in set(text3) if wd.istitle() and len(wd) > 10]) 
# 长度大于10的句首词
>>> sorted([w for w in set(sent7) if not w.islower()])
# 非全部小写的词
>>> sorted([t for t in set(text2) if 'cie' in t or 'cei' in t])
# 含‘cie’或‘cei’的词
```

> 4.这个例子稍微有些复杂:将所有纯字母组成的词小写。也许只计数小写的词会更简单一 
>
> 些，但这却是一个错误的答案(为什么?)。 

原文是“This example is slightly complicated: it lowercases all the purely alphabetic items. Perhaps it would have been simpler just to count the lowercase-only items, but this gives the wrong answer (why?).”

意思是说，上述操作为了得到所有词的集合，将所有的纯字母单词变成了小写才进行计数，那为什么不直接进行只含小写字母单词的计数呢？

很明显，因为有些词在文本中出现但不一定存在全部小写的形式。