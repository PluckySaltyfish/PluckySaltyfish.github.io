---
layout: post
title: "NLP with Python观察笔记(5)"
date: 2018-09-25 02:47:56
description: 练习2.8
tags: 
 - NLP
---

### 2.8练习

> 创建一个变量 phrase 包 一个词的链表。实验本章描述的操作，包括加法、乘法、 索引、切片和排序。

  ```
略
  ```

>  使用语料库模块处理 austen-persuasion.txt。这书中有多少词标识符?多少词类型?

```python
# 词标识符是指一共有多少个词，词类型指的是一共有多少个不同的词
>>> from nltk.corpus import gutenberg
>>> len(gutenberg.words('austen-persuasion.txt'))
98171
>>> len(set('austen-persuasion.txt'))
13
```

> 使用布朗语料库阅读器 nltk.corpus.brown.words()或网络文语料库阅读器 nltk.corpus.webtext.words()来访问两个不同文体的一些样例文。

```python
略
```

> 使用 state_union 语料库阅读器，访问《国情咨文报告》的文本 。计数每个文档中 出现的 men、women 和 people。随时间的推移这些词的用法有什么变化? 

```python
>>> from nltk.corpus import state_union
>>> words = ['men','women','people']
>>> cfd = nltk.ConditionalFreqDist((word,fileid[:4]) for fileid in state_union.fileids() for w in state_union.words(fileid) for word in words if w.lower().startswith(word))
>>> cfd.plot()
```

![img]({{ site.baseurl | prepend:site.url}}/images/stateunion.png){: .center-image }

> 考查一些名词的整体部分关系。请记住，有 3 种整体部分关系，所以你需要使用 me mber_meronyms()，part_meronyms()，substance_meronyms()，member _holonyms(), part_holonyms()以及 substance_holonyms()。 

```python
>>> wn.synset("wood.n.01").substance_meronyms()
[Synset('lignin.n.01')]
# 木质素是木头的本质
>>> wn.synset("forest.n.01").member_meronyms()
[Synset('tree.n.01'), Synset('underbrush.n.01')]
# 森林包括树和灌木
>>> wn.synset("computer.n.01").part_meronyms()
[Synset('busbar.n.01'), Synset('cathode-ray_tube.n.01'), Synset('central_processing_unit.n.01'), Synset('chip.n.07'), Synset('computer_accessory.n.01'), Synset('computer_circuit.n.01'), Synset('data_converter.n.01'), Synset('disk_cache.n.01'), Synset('diskette.n.01'), Synset('hardware.n.03'), Synset('keyboard.n.01'), Synset('memory.n.04'), Synset('monitor.n.04'), Synset('peripheral.n.01')]
# 计算机的组成部分
>>> wn.synset("people.n.01").member_holonyms()
[Synset('world.n.08')]
# 世界由人组成
>>> wn.synset("carbon.n.01").substance_holonyms()
[Synset('coal.n.01'), Synset('limestone.n.01'), Synset('petroleum.n.01')]
# 含碳物质由碳组成
>>> wn.synset("apple.n.01").part_holonyms()
[Synset('apple.n.02')]
# apple的第二个意思是苹果树，苹果是苹果树的一部分
>>> wn.synset("people.n.01").substance_meronyms()
[]
# Σ(⊙▽⊙"a不应该是复读机吗
```



> 在比较词表的讨论中，我们创建了一个对象叫做 translate，通过它你可以使用德语和意大利语词汇查找对应的英语词汇。这种方法可能会出现什么问题?你能提出一个办法来避免这个问题吗? 

```python
# https://www.bbsmax.com/A/gVdnYR1Q5W/
参考这个吧，虽然我觉得不一定是作者的原意
```

> 根据 Strunk 和 White 的《Elements of Style》，词 however 在句子开头使用是“in wh atever way”或“to whatever extent”的意思，而没有“nevertheless”的意思。他们给出了正确用法的例子:However you advise him,he will probably do as he thinks bes t.(http://w ww.bartleby.com/141/strunk3.html)。使用词汇索引工具在我们一直在思考的各种文中研究这个词的实际用法。也可以看 LanguageLog 发布在 http://itre.cis.upenn. edu/~myl/languagelog/archives/001913.html 上的“Fossilized prejudices abou‘t however’”。 

```
略
```

> 在名字语料库上定义一个条件频率分布，显示哪个首字母在男性名字中比在女性名字中更常用(见图 2-7)。

```python
>>> cfd = nltk.ConditionalFreqDist((fileid,initial[0].upper())for fileid in names.fileids() for initial in names.words(fileid))
>>> cfd.plot() # 如下图
>>> for i in range(65,65+26):
...     if cfd['female.txt'][chr(i)] < cfd['male.txt'][chr(i)]:
...             list.append([chr(i)])
...
>>> list
[['H'], ['Q'], ['U'], ['W'], ['X']]
```

![img]({{ site.baseurl | prepend:site.url}}/images/names.png){: .center-image }

> 挑选两个文章 ，研究它们之间在词汇、词汇丰富性、文体等方面的差异。你能找出几 个在这两个文中词意相当不同的词吗?例如:在《白鲸记》与《理智与情感》中的 monstrous。 

```
暂时做不了
```

> 阅读 BBC 新闻文章:“UK’s Vicky Pollards ‘left behind’”http://news.bbc.co.uk/1/ hi/education/6173441.stm。文章给出了有关青少年语言的以下统计:“使用最多的 20 个 词，包括 yeah, no, but 和 like，占所有词的大约三分之一”。对于大量文 源来说，所 有词标识符的三分之一有多少词类型?你从这个统计中得出什么结论?更多相关信息 请阅读 LanguageLog 上的 http://itre.cis.upenn.edu/~myl/languagelog/archives/003993.html。 

```
略
```



> 调查模式分布表寻找其他模式。试着用你自己对不同文体的印象理解来解释它们。 你能找到其他封闭的词汇归类，展现不同文体的显著差异吗? 
>
> Investigate the table of modal distributions and look for other patterns. Try to explain them in terms of your own impressionistic understanding of the different genres. Can you find other closed classes of words that exhibit significant differences across different genres?
>
> （观察情态动词分布表寻找其他规律）

![img]({{ site.baseurl | prepend:site.url}}/images/modal.png){: .center-image }

```python
# 兴趣类中出现最多的是can，科幻片中极少出现may
# 寻找词汇类['what','when','where','who','why']在不同类别中出现的规律
>>> import nltk
>>> from nltk.corpus import brown
>>> words = ['what','when','where','who','why']
>>> cfd = nltk.ConditionalFreqDist((genre,word)for genre in brown.categories() for word in brown.words(categories=genre) )
>>> cfd.tabulate(samples = words)
                 what  when where   who   why
      adventure   110   126    53    91    13
 belles_lettres   244   252   107   452    36
      editorial    84   103    40   172    10
        fiction   128   133    76   103    18
     government    43    56    46    74     6
        hobbies    78   119    72   103    10
          humor    36    52    15    48     9
        learned   141   227   118   212    20
           lore   130   182    97   259    25
        mystery   109   114    59    80    25
           news    76   128    58   268     9
       religion    64    53    20   100    14
        reviews    44    54    25   128     9
        romance   121   126    54    89    34
science_fiction    27    21    10    13     4
# 可以观察出许多规律，比如说优美的书信里这次问词出现的非常多
```

> CMU 发音词典包含某些词的多个发音。它包含多少种不同的词?具有多个可能的发音的词在这个词典中的比例是多少? 

```python
>>> entries = nltk.corpus.cmudict.entries()
>>> total = [x[0] for x in entries]
>>> fdist = nltk.FreqDist(total)
>>> len(set(total))
123455 # 包含123455个不同的词
>>> duplicate = [x for x in set(total) if fdist[x]>1]
>>> len(duplicate)
9241 # 多音词有9241
>>> len(duplicate)/len(set(total))
0.07485318537118789 # 比例
```

> 没有下位词的名词同义词集所占的百分比是多少?你可以使用 wn.all_synsets('n') 得到所有名词同义词集。 

```python
>>> for n_set in wn.all_synsets('n'):
...     total = total + 1
...     if(len(n_set.hyponyms())==0):
...             count1 = count1 + 1
...
>>> count1/total
0.7967119283931072
```

> 定义函数 supergloss(s)，使用一个同义词集 s 作为它的参数，返回一个字符串，包含 s 的定义和 s 所有的上位词与下位词的定义的连接字符串。 

```python
>>> def supergloss(s):
...     sent = 'Definition:'+s.definition()
...     sent+= 'Hyponyms:'+str(s.hyponyms())
...     return sent
```

> 写一个程序，找出所有在布朗语料库中出现至少 3 次的词。 

```python
>>> from nltk.corpus import brown
>>> fdist = nltk.FreqDist(brown.words())
>>> a = []
>>> for word in list(fdist.keys()):
    	if(fdist[word]>=3):
            a.append(word)
```

> 写一个程序，生成如表 1-1 所示的词汇多样性得分表(例如:标识符/类型的比例)。 包括布朗语料库文体的全集(nltk.corpus.brown.categories())。哪个文体词汇多样性最低(每个类型的标识符数最多)?这是你所期望的吗? 

```python
>>> for category in brown.categories():
...     print(category,"\t",lexical_diversity(brown.words(categories=category)))
...
adventure 	 7.814063556457065
belles_lettres 	 9.396666847619565
editorial 	 6.22891809908999
fiction 	 7.362717695119329
government 	 8.570712626818237
hobbies 	 6.899455383326351
humor 	 4.324297388877816
learned 	 10.788777507562726
lore 	 7.60525408536165
mystery 	 8.188054998567745
news 	 6.98582742809504
religion 	 6.182174799937235
reviews 	 4.718757245536749
romance 	 8.284666351159489
science_fiction 	 4.475719146303742
```

> 写一个函数，找出一个文中最常出现的 50 个词，停用词除外。 

```python
>>> def most_common_50(text1):
...     content = [w for w in text1 if w.lower() not in stopwords.words('english')]
...     fdist = nltk.FreqDist(content)
...     return fdist.most_common(50)
```

> 写一个程序，输出一个文中5个最常见的双连词(相邻词对)，忽略停用词的双连词。 
>

```python
def most_common_50(sent):
	pair = nltk.bigrams(sent)
	pair1 = []
	for item in pair:
		if item[1].lower() in stopwords.words('english') or item[0].lower() in stopwords.words('english'):
			continue
		pair1.append(item)
	return pair1
```

> 写一个程序，按文体创建一个词频表，以 2.1 节给出的词频表为范例，选择你自己的词汇，并尝试找出那些在一个文体中很突出或很缺乏的词汇。讨论你的研究结果。



> 1. 写一个函数 word_freq()，用一个词和布朗语料库中的一个部分的名字作为参数， 
>
>     ```
>       计算这部分语料中词的频率。
>     ```
>
> 2. 写一个程序，估算一个文 中的音节数，利用 CMU 发音词典。 
>
> 3. 定义一个函数 hedge(text)，处理一个文 和产生一个新的版 在每三个词之间插 
>
>     入一个词 like。 
>
> 86 
>
> 1. ●齐夫定律:f(w)是一个自由文 中的词 w 的频率。假设一个文 中的所有词都按照它 们的频率排名，频率最高的在最前面。齐夫定律指出一个词类型的频率与它的排名成反 比(即 f×r=k，k 是某个常数)。例如:最常见的第 50 个词类型出现的频率应该是最常 见的第 150 个词型出现频率的 3 倍。 
>
>    1. 写一个函数来处理一个大文 ,使用 pylab.plot 画出相对于词的排名的词的频率。 你认可齐夫定律吗?(提示:使用对数刻度会有帮助。)所绘的线的极端情况是怎 样的? 
>    2. 随机生成文 ，如:使用 random.choice("abcdefg ")，注意要包括空格字符。 你需要事先 import random。使用字符串连接操作将字符累积成一个很长的字符 串。然后为这个字符串分词，产生前面的齐夫图，比较这两个图。此时你怎么看齐 夫定律? 
>
> 2. ●修改例 2-1 的文 生成程序，进一步完成下列任务: 
>
>    1. 在一个词链表中存储 n 个最相似的词，使用 random.choice()从链表中随机选取 
>
>       一个词。(你将需要事先 import random) 
>
>    2. 选择特定的文体，如:布朗语料库中的一部分或者《创世纪》翻译或者古腾堡语料 
>
>       库中的文 或者一个网络文 。在此语料上训练一个模型，产生随机文 。你可能 要实验不同的起始字。文 的可理解性如何?讨论这种方法产生随机文 的长处和 短处。 
>
>    3. 现在使用两种不同文体训练你的系统，使用混合文体文 做实验。讨论你的观察结 果。 
>
> 3. ●定义一个函数 find_language() ，用一个字符串作为其参数，返回包 这个字符串 作为词汇的语言的列表。使用《世界人权宣言》(udhr)的语料，将你的搜索限制在 L atin-1 编码的文件中。 
>
> 4. ●名词上位词层次的分枝因素是什么?也就是说，对于每一个具有下位词——上位词层 次中的子女——的名词同义词集，它们平均有几个下位词?你可以使用 wn.all_synse ts('n')获得所有名词同义词集。 
>
> 5. ●一个词的多义性是它所有 义的个数。利用 WordNet，使用 len(wn.synsets('dog', 'n'))我们可以判断名词 dog 有 7 种 义。计算 WordNet 中名词、动词、形容词和副词 
>
>    的平均多义性。 
>
> 6. ●使用预定义的相似性度量之一给下面的每个词对的相似性打分。按相似性减少的顺序 
>
>    排名。你的排名与这里给出的顺序有多接近?(Miller & Charles, 1998)实验得出的顺 序:car-automobile, gem-jewel, journey-voyage, boy-lad, coast-shore, asylum-madhouse, magician-wizard, midday-noon, furnace-stove, food-fruit, bird-cock, bird-crane, tool-imp lement, brother-monk, lad-brother, crane-implement, journey-car, monk-oracle, cemetery- woodland, food-rooster, coast-hill, forest-graveyard, shore-woodland, monk-slave, coast-f orest, lad-wizard, chord-smile, glass-magician, rooster-voyage, noon-string.  
