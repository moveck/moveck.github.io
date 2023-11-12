
---
title: python笔记_part.1
tags:
  - techniques
date: 2023-07-07
lastmod: 2023-11-12
categories:
  - techniques
description: "简介"
---

关于isinstance的额外用法：
判断一个值是否为int，float中的一种：`isinstance(value,(int,float))`

setattr的使用方法：`setattr(a,"y","11")`

`__slots__`对子类是没有用的！使用它时记得加上“引号”。
给实例加上方法，库：`from types import MethodType`

生成器：一个是函数，一个是对象。这是不同的方式！对象不必使用`yield`，因为对象本身`next`已经拥有了循环的标准，用`return`返回即可，示范：
```py
class test(object):
    ...
    def __next__(self):
        self.a, self.b = self.b, self.a + self.b # 计算下一个值
        if self.a > 100000: # 退出循环的条件
            raise StopIteration()
        return self.a 
        # 返回下一个值，相当于yield，next

def test(a):
    b,c=0,1
    for n in range(a):
        b,c=c,b+c
        yield b
```
看出区别了吗？函数需要加一个值！没有该怎么办呢？
正确示范：
```py
def test():
    a,b=0,1
    while True:
        a,b=b,a+b
        yield a
        #yield是用来中间截取的。
```

`b`是读取二进制的意思。  
如果只用`r`来读取文件，默认使用系统的字符集设置。

英文国家为`ascii`，就是只有英文。  
中文国家为`gbk`  
通常文件使用`utf-8`，也就是中文加英文。  
`b`是读取二进制的意思。 

文件过大怎么办？  
`read(size)`可以读取`size`个字节。  
每调用一次`readline()`就可以读取一行的内容。  
在给文档进行尾部添加时，可以直接使用`a`。  
  
给参数注释：
`def test(value1:list,value2:list)->list:`

递归：  
递归，就是将一个方法无限重复。一般在需要循环时使用。经常可以用到。例：
```py
def test(a):
    if a==1:
        return 1 #一个限制，否则将一直循环-1。
    return a+test(a-1)
```
  
