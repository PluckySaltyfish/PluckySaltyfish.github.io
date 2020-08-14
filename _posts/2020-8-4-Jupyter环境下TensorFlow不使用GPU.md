---
layout: post
title: "Jupyter环境下TensorFlow不使用GPU"
date: 2020-08-04 12:13:06
description: os.environ["CUDA_VISIBLE_DEVICES"] = "2,3"
tags:
 - 错误记录
---
### 

一训练和推理jupyter就闪断，也不报错，估测是没连上GPU，果然，加了以下这个就好了

```python
os.environ["CUDA_VISIBLE_DEVICES"] = "2,3"
```

