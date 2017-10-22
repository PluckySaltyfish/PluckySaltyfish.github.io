---
layout: post
title: "嘿,Siri：基于设备神经网络驱动语音触发器的苹果个人助理"
date: 2017-10-22 04:49:18
description: 苹果发布的如何实现“嘿，Siri”的随时唤醒功能。
tags:
 - Machine learning
 - 翻译
---
> 本文翻译自[Apple Machine Learning Journal](https://machinelearning.apple.com/2017/10/01/hey-siri.html)
{: .note}

>“嘿，Siri”功能，让用户不用按键就可以唤醒语音助手Siri。这是因为苹果的处理器集成了非常小的语音识别装置，这个装置一直保持运行，等待着用户说出“嘿，Siri”。当它检测到用户说出这两个词后，Siri将会将后面的语音处理为命令或者查询。“嘿Siri”检测使用深层神经网络（Deep Neural Network ，简称DNN），将每个时刻的声音模型转换成语音的概率分布，并使用时间集成来计算这个声音是“嘿，Siri”的置信度。如果置信度分数足够高，Siri就将被唤醒。本文介绍一些实现此功能的基础技术，主要面向了解一些机器学习，但对语言识别没有了解的读者。

#### 不用手就唤醒Siri
当你需要Siri帮助的时候，不需按键，仅仅说出“嘿Siri”就可以唤醒Siri。这一功能看上去简单，但想快速高效地唤醒Siri，是需要花不少功夫的。“嘿Siri”通过软件，硬件，网络服务高效结合工作，以给用户提供一个良好的体验。

