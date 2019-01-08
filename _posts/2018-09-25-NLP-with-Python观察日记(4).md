---
layout: post
title: "NLP with Python观察笔记(4)"
date: 2018-09-25 02:47:56
description: 2.1-2.5
tags: 
 - NLP
---

### 一些语料库

##### 古腾堡语料库

电子小说及文学作品。

```
nltk.corpus.gutenberg
```

**网络聊天文本**

论坛、剧本、评论、偶然听到的话

```
nltk.corpus.webtext
```

即时消息聊天语料库

```
nltk.corpus.nps_chat
```

**布朗语料库**

布朗大学收集的百万级别的英语电子语料库

用来研究文体之间的差异

```
nltk.corpus.brown
```

**路透社语料库**

新闻文档

```
nltk.corpus.reuters
```

**就职演说语料库**

按时间顺序存储的总统演讲

```
nltk.corpus.inaugural
```

**发音词典**

```
nltk.corpus.cmudict
```

**比较词表**

很多语言的同源词

```
nltk.corpus.swadesh
```

**词汇语料库**

常见词词典，可用于检查词汇的拼写

```
nltk.corpus.words
```

**停用词语料库**

```
nltk.corpus.stopwords
```

**WordNet**

面向语义的英文语料库

```
nltk.corpus.wordnet
```



### 一些语料库的方法

```python
.words(fileid) # 获取单词
.sents(fileid) # 获取句子
.raw(fileid) # 获取原始文本，包括空格等符号
.fileids() # 获取文件id

# 不同语料库还有特殊的方法，如brown等含分类语料库有categories
brown.categories()
words = brown.words(categories)
```



### 习题

> 轮到你来:选择布朗语料库的不同部分，修改前面的例子，计数包  wh 的词，如:what，when，where，who 和 why 

```python
>>> adventure =  brown.words(categories = 'adventure')
>>> wh = ['what','where','when','who','why']
>>> fdist = nltk.FreqDist([w.lower() for w in adventure])
>>> for i in wh:
...     print(i,':',fdist[i],end =' ')
...
what : 149 where : 58 when : 173 who : 95 why : 30 >>>
```

> 轮到你来:处理 布朗语 料库的 新闻和 言情文 体，找出 一周中 最有新 闻价值 并且是 最浪漫的日子。定义一个变量 days 包 星期的链表，如['Monday', ...]。然后使用 cfd.tabulate(samples=days)为这些词的计数制表。接下来用绘图替 代制表尝试同样的事情。你可以在额外的参数 conditions=['Monday', ...]的 帮助 下控制 星期输出的顺 序。 

```python
>>> from nltk.corpus import brown
>>> days = ['Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday']
>>> categories = ['news','romance']
>>> cfd = nltk.ConditionalFreqDist((category,day) for category in categories for day in days for w in brown.words(categories = category) if w.startswith(day))
>>> cfd.plot()
```

![img]({{ site.baseurl | prepend:site.url}}/images/days.png){: .center-image }

#### 发音词典

```python
# 你可以总结一下下面的例子的 功能，并解释它们是如何实现的?
>>> [w for w, pron in entries if pron[-1] == 'M' and w[-1] == 'n']
['autumn', 'column', 'condemn', 'damn', 'goddamn', 'hymn', 'solemn']
# n在末尾不发音的词
>>> sorted(set(w[:2] for w, pron in entries if pron[0] == 'N' and w[0] != 'n'))
['gn', 'kn', 'mn', 'pn']
# 第一个字母不发音，发n的音的词
```

#### WordNet

>轮到你来:Write down all the senses of the word dish that you can think of. Now, explore this word with the help of WordNet, using the same operations we used above.

```python
>>> for synset in wn.synsets('dish'):
...     print(synset.lemma_names(),':',synset.definition())
...
['dish'] : a piece of dishware normally used as a container for holding or serving food
['dish'] : a particular item of prepared food
['dish', 'dishful'] : the quantity that a dish will hold
['smasher', 'stunner', 'knockout', 'beauty', 'ravisher', 'sweetheart', 'peach', 'lulu', 'looker', 'mantrap', 'dish'] : a very attractive or seductive looking woman
['dish', 'dish_aerial', 'dish_antenna', 'saucer'] : directional antenna consisting of a parabolic reflector for microwave or radio frequency radiation
['cup_of_tea', 'bag', 'dish'] : an activity that you like or at which you are superior
['serve', 'serve_up', 'dish_out', 'dish_up', 'dish'] : provide (usually but not necessarily food)
['dish'] : make concave; shape like a dish
```

