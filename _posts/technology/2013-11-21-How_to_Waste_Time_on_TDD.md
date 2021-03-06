---
layout: page  
title: How to Waste Time on TDD   
category: 技术  
tags: TDD   
---
{% include JB/setup %}

翻译作品，原文请点击：[http://andrzejonsoftware.blogspot.ie/2012/06/how-to-waste-time-on-tdd.html](http://andrzejonsoftware.blogspot.ie/2012/06/how-to-waste-time-on-tdd.html)

(这篇博客最早是由Piotr Wlodarek在他的TheSingularity.pl发表的。我非常喜欢它所以将它翻译成了英文，这样就能有更多的人读到它啦。)

有些人抱怨TDD(Test-Driven Development)拖慢了他们的研发流程。如果你也想步他们的后尘,那么你应该这么做:

1. 写完生产代码之后才开始写测试代码    
2. 从不先考虑设计，而是忙不迭的扎进TDD流程中，到了需要时才临时进行设计。你就有机会反复的修改代码和测试架构。   
3. 学会完全依靠自己去覆盖测试场景，不用费力去看任何教学视频，也不用去读任何这方面主题的书。     
4. 保证你的测试在开始运行前至少加载半分钟。只要你用过时蹩脚的硬盘驱动，完全不遗漏的加载所有框架代码。   
5. 保证所有功能点都是用网络浏览器，或者桌面图形窗口进行测试的。      
6. 保证所有的测试都依赖数据库。       
7. 只能通过手工查找对应的测试和生产代码。        
8. 频繁切换桌面、窗口、tab键，只是为了找到测试的启动脚本。       
9. 尝试写尽可能少的类，保证每个类中都包含了一堆不相关的属性。这些类一定可以成为测试的噩梦。       
10. 在Cucumber中定义非常漂亮的步骤，尽管你的客户压根不想读你的特性描述(或者可能你目前根本找不到一个客户)。





























