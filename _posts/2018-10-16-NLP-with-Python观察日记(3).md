---
layout: post
title: "NLP with Python观察笔记(3)"
date: 2018-09-25 02:47:56
description: 练习1.8
tags: 
 - NLP
---

### 1.8练习

> 尝试使用 Python 解释器作为一个计算器，输入表达式，如 12/(4+1)。 

```
略
```

> 26 个字母可以组成 26 的 10 次方或者 26**10 个 10 字母长的字符串。也就是 1411 67095653376L (结尾处的 L 只是表示这是 Python 长数字格式 )。100 个字母长度的 
>
> 字符串可能有多少个? 

```
26**100
```

> Python 乘法运算可应用于链表。当你输入 ['Monty', 'Python'] * 20 或者 3 * se 
>
> nt1 会发生什么? 

```
获得一个重复了乘数的list。

如['Monty', 'Python'] * 20变成['Monty', 'Python','Monty', 'Python',...,'Monty', 'Python']一共重复20次

```

> 复习 1.1 节关于语言计算的内容。在 text2 中有多少个词?有多少个不同的词? 

```python
>>> len(text2)
141576
>>> len(set(text2))
6833
```



> 比较表格 1-1 中幽默和言情小说的词汇多样性得分，哪一个文体中词汇更丰富? 

```
言情小说
```

> 制作《理智与情感》中四个主角:Elinor，Marianne，Edward 和 Willoughby 的分布图。 
>
> 在这部小说中关于男性和女性所扮演的不同角色，你能观察到什么?你能找出一对夫妻 
>
> 吗? 

```python
text2.dispersion_plot(['Elinor','Marianne','Edward','Willoughby'])
```

![img]({{ site.baseurl | prepend:site.url}}/images/Figure_1_1.png){: .center-image }

```
Elinor和Marianne应该是一对夫妻
```

> 查找 text5 中的搭配

```python
>>> text5.collocations()
wanna chat; PART JOIN; MODE #14-19teens; JOIN PART; PART PART;
cute.-ass MP3; MP3 player; JOIN JOIN; times .. .; ACTION watches; guys
wanna; song lasts; last night; ACTION sits; -...)...- S.M.R.; Lime
Player; Player 12%; dont know; lez gurls; long time
```

> 思考下面的 Python 表达式:len(set(text4))。说明这个表达式的用途。描述在执行此计算中涉及的两个步骤。

```
用处：计算text4的词汇量
先通过set(text4)将单词去重
再通过len(set(text4))计算长度
```

> 复习 1.2 节关于链表和字符串的内容。 
>
> ​	 定义一个字符串，并且将它分配给一个变量，如:my_string = 'My String'(在 字符串中放一些更有趣的东西)。用两种方法输出这个变量的内容，一种是通过简单地输入变量的名称，然后按回车;另一种是通过使用 print 语句。 

```
略
```

> ​	尝试使用 my_string+ my_string 或者用它乘以一个数将字符串添加到它自身， 例如:my_string* 3。请注意，连接在一起的字符串之间没有空格。怎样能解决 这个问题? 

```python
>>> my_string = 'My String'
>>> my_string = my_string + ' '
>>> my_string = my_string*3
>>> my_string = my_string[:-1]
>>> my_string
'My String My String My String'
```

> ​	使用的语法 my_sent = ["My", "sent"]，定义一个词链表变量 my_sent(用你自己的词或喜欢的话)。 
>
> 1. 使用' '.join(my_sent)将其转换成一个字符串。 
> 2. 使用 split()在你指定的地方将字符串分割回链表。 

```
略
```

> ​	定义几个包含词链表的变量，例如: phrase1，phrase2 等。将它们连接在一起组 成不同的组合(使用加法运算符)，最终形成完整的句子。len(phrase1 + phrase2) 与 len(phrase1) + len(phrase2)之间的关系是什么? 

```
相等
```

> 考虑下面两个具有相同值的表达式。哪一个在 NLP 中更常用?为什么? 
>
> 1. "Monty Python"[6:12] 
> 2. ["Monty", "Python"]\[1]

```
第二个吧，直观
```

> 我们已经看到如何用词链表表示一个句子，其中每个词是一个字符序列。sent1\[2]\[2] 代表什么意思?为什么?请用其他的索引值做实验。 

```
sent1中第3个词中的第3个字母
```

> 在变量 sent3 中保存的是 text3 的第一句话。在 sent3 中 the 的索引值是 1，因为 sent3\[1]的值是“the”。sent3 中“the”的其它出现的索引值是多少? 

```
这题的意思应该是直接数吧，5和8
```

> 复习 1.4 节讨论的条件语句。在聊天语料库(text5)中查找所有以字母 b 开头的词。 按字母顺序显示出来。 

```python
>>> sorted([w for w in text5 if w.startswith('b')])
```

> 在 Python 解释器提示符下输入表达式 range(10)。再尝试 range(10, 20), range (10, 20, 2)和 range(20, 10, -2)。在后续章节中我们将看到这个内置函数的更多用途。 

```
这个和切片的规则一样
```

> 使用 text9.index()查找词 sunset 的索引值。你需要将这个词作为一个参数插入到圆括号之间。通过尝试和出错的过程中，找到完整的句子中包含这个词的切片。 

```python
text9[613:644]
```

> 使用链表加法、set 和 sorted 操作，计算句子 sent1...sent8 的词汇表。 

```python
sorted(set(sent1))
```

> 下面两行之间的差异是什么?哪一个的值比较大?其他文本也是同样情况吗? 
>
> \>>> sorted(set([w.lower() for w in text1])) 
>
> \>>> sorted([w.lower() for w in set(text1)] )

```python
第二个中会有重复的词存在（存在原来是大写的词和是小写的重复），第二个多。
```

> w.isupper()和 not w.islower()这两个测试之间的差异是什么? 

```
后者会包括非全字母字符串
```

> 写一个切片表达式提取 text2 中最后两个词。 

```python
text2[-2::]
```

> 找出聊天语料库(text5)中所有四个字母的词。使用频率分布函数( FreqDist)， 以频率从高到低显示这些词。

```python
a = FreqDist([w for w in text5 if len(w)==4])
a.most_common(len(a))
```

> 复习 1.4 节中条件循环的讨论。使用 for 和 if 语句组合循环遍历《巨蟒和圣杯》(tex 
>
> t6 )的电影剧本中的词，输出所有的大写词，每行输出一个。 

```python
for w in text6:
    if w.isupper():
        print(w)
```

> 写表达式找出 text6 中所有符合下列条件的词。结果应该是词链表的形式: ['word 
>
> 1', 'word2', ...]。 

> 1. 以ize结尾 
> 2. 包含字母 z 
> 3. 包含字母序列 pt 
> 4. 除了首字母外是全部小写字母的词(即 titlecase) 

```python
#1
[w for w in text6 if w.endswith('ize')]
#2
[w for w in text6 if 'z' in w]
#3
[w for w in text6 if 'pt' in w]
#4
[w for w in text6 if w[0].isupper() and w[1::].islower()]
```

> 定义 sent 为词链表['she', 'sells', 'sea', 'shells', 'by', 'the', 'sea', 'shore']。 编写代码执行以下任务: 
>
> 1. 输出所有 sh 开头的单词 
> 2. 输出所有长度超过 4 个字符的词 

```python
>>> sent = ['she', 'sells', 'sea', 'shells', 'by', 'the', 'sea', 'shore']
>>> for w in sent:
...     if w.startswith('sh'):
...             print(w)
...
she
shells
shore
>>> for w in sent:
...     if len(w)>4:
...             print(w)
...
sells
shells
shore
```

> 下面的 Python 代码是做什么的? sum([len(w) for w in text1]) ，你可以用它来 算出一个文本的平均字长吗? 

```
sum([len(w) for w in text1]) /len(tex1)
```

> 定义一个名为 vocab_size(text)的函数，以文本作为唯一的参数，返回文本的词汇量。 

```python
def vocab_size(text):
    return len(set(text))
```

> 定义一个函数 percent(word, text)，计算一个给定的词在文本中出现的频率，结果以百分比表示。

```python
def percent(word,text):
    fdist = FreqDist(text)
    return str(fdist['the']/len(text1)*100) + '%'
```

