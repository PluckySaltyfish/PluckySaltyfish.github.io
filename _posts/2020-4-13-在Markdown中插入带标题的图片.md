---
layout: post
title: "Alfred-在Markdown中插入带标题的图片"
date: 2020-04-13 12:32:36
description: Workflow开发2
tags:
 - Alfred Workflow
 - Python
---
>在很多Markdown的编辑器中，比如说Typora，在插入图片时并不能够自动把图片的文件名显示成图片的title，这次写了一个Alfred的workflow可以在Markdown编辑器中插入带图片的标题

### 实现思路

- 触发：KeyWord + 参数（指定图片路径、编号、标题、缩放大小）。
- python读取参数，放入html的模板中。
- Copy to clipboard

### 环境

- Python2.7

### 基本配置

- 流程

![img]({{ site.baseurl | prepend:site.url}}/images/img-1.png){: .center-image }*图1 流程*

- Script Filter

![img]({{ site.baseurl | prepend:site.url}}/images/img-2.png){: .center-image }*图2*

- Copy to Clipborad

![img]({{ site.baseurl | prepend:site.url}}/images/img-3.png){: .center-image }*图3*

### Python代码
```python
# encoding: utf-8

import sys
import time
from workflow import Workflow
reload(sys)
sys.setdefaultencoding('utf8')

def generate_text(location,number,title,zoom):
	return '<center><img style="border-radius: 0.3125em;box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);zoom:'+ zoom + '" src="'+location+'"><br><div style="border-bottom: 1px solid #d9d9d9;display: inline-block;color: #000;padding: 2px;">图'+number+' '+title+'</div></center>'

def main(wf):
    if len(wf.args) < 4:
    	zoom = '67%'
    else:
    	zoom = wf.args[3] + '%'
    if len(wf.args) < 3:
    	t = ''
    else:
    	t = wf.args[2]
    if len(wf.args) < 2:
    	num = 1
    else:
    	num = wf.args[1]
    if len(wf.args) < 1:
    	location = ''
    else:
    	location = wf.args[0]
    hint_text ='位置:'+ location + ',编号:' + str(num) +',标题:' + t + ',缩放:' + zoom
    text = generate_text(location,str(num),t,str(zoom))
    wf.add_item(title=hint_text,subtitle="参数用空格分隔",arg=text,valid=True)
    wf.send_feedback()

if __name__ == u"__main__":
    wf = Workflow()
    sys.exit(wf.run(main))
```


### 知识点

学会了传参，通过wf.arg获取传递的参数。

### 最终效果图

![img]({{ site.baseurl | prepend:site.url}}/images/aw-img.gif){: .center-image }*图4 最终结果*