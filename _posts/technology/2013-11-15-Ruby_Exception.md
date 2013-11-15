---
layout: page  
title: Ruby Exception  
category: 技术  
tags: Ruby   
---
{% include JB/setup %}

在Ruby中，我们用raise方法来创建一个表示异常的对象。  
raise有四种使用方法：

- raise 
产生一个错误信息为空的RuntimeError(default for raise)
- raise "Exception"
产生一个错误信息为"Exception"的RuntimeError
- raise TypeError, "Exception"
产生一个错误信息为"Exception"的TypeError
- raise TypeError, "Exception", arr
产生一个错误信息为"Exception"的TypeError，arr保存backtrace信息

通过rescue可以捕获Exception  
如果rescue后面没有跟参数，则默认捕获StandardError.(所以，如果想自定义Exception，一般继承StandardError比较合适)

在block中raise的最近一次的error会保存在$!全局变量中。在rescue中，通过比较parameter === $!(===除了表示通常的==的含义,也表示当后面的参数为前面参数或其子类的实例..., 则判断为true；或者说，前面的参数为后面的类或者父类..., 则判断为true) 来判断是否应该捕获此异常(如果没有parameter则默认为StandardError)

如果rescue后面的parameter是raised exception的class或者superclass，则匹配成功。



