---
layout: post
title: "Python中classmethod"
date: 2021-02-14 03:49:30
description: 类中用classmethod装饰的函数是什么意思？
tags:
 - Python
---

### 问题说明

在阅读`openNMT`源码的时候发现很多类方法的头部用`@classmethod`做了装饰，查找资料发现这可以看做是一种静态方法，在类没有初始化的时候就能使用。
  
> 很有道理，现在想想pytorch有一些方法直接用torch.method()出来的应该就是静态方法。
{: .note}

### 定义
```python
class A(object):

    # 属性默认为类属性（可以给直接被类本身调用）
    num = "类属性"

    # 实例化方法（必须实例化类之后才能被调用）
    def func1(self): # self : 表示实例化类后的地址id
        print("func1")
        print(self)

    # 类方法（不需要实例化类就可以被类本身调用）
    @classmethod
    def func2(cls):  # cls : 表示没用被实例化的类本身
        print("func2")
        print(cls)
        print(cls.num)
        cls().func1()

    # 不传递传递默认self参数的方法（该方法也是可以直接被类调用的，但是这样做不标准）
    def func3():
        print("func3")
        print(A.num) # 属性是可以直接用类本身调用的
```

可以看出以下规则：
- 静态方法用`@classmethod`装饰，在类没有实例化时可以直接调用
- 静态方法不用传入类的实例化对象`self`，而是传入一个默认参数`cls`，即没有实例化的类本身。
> 我以前看源码就发现这个cls很蹊跷，全文到处没有定义，知道是默认参数，但我一直以为是什么Bert(transformer)里的那个cls位标签......
{: .note}