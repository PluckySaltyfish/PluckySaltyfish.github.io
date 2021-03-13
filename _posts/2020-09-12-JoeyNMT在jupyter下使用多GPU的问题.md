---
layout: post
title: "Joeynmt在jupyter下使用多gpu的问题"
date: 2020-09-12 04:31:22
description: joeynmt的multi-gpu使用心得
tags:
 - 错误记录
---
### 问题描述
`joeynmt`最新的版本实现了muli-gpu的方案,其实现方式就是把一个batch里的所有样本平均分配给各个GPU，比如我设置的`batch_size=1024`,我一共有`4`块gpu，那么每个batch每块GPU就要跑`256`个样本。

之前用的`open-nmt`的multi-gpu，我观察到的应该是当一块满了之后再用下一块，并不是平均分。所以`joeynmt`使用时需要设置可见GPU（配置文件里并没有直接设置），保证每一块卡上的平均显存都要够。

### pytorch设置可见GPU
由于我一开始使用的是`jupyter`，所以不同于以往的在命令行中设置可见，是想直接在其环境里设置可见gpu，所以查询了pytorch设置可见GPU的方法：
```python
import os
os.environ["CUDA_VISIBLE_DEVICES"] = '0,1,2,3'

# 还有一种不推荐的
torch.cuda.set_device(0)
```

### 结果
结果没用，不管哪种方法，`joeynmt`还是给我把8块卡都能找到。最后我还是写成Python文件在命令行里跑了。

