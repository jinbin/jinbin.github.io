---
layout: page  
title: The Smallest Distributed System (3)   
category: 技术   
tags: 持续集成    
---
{% include JB/setup %}


##最小的分布式系统(3)

![架构图8](/image/The_Smallest_Distributed_System_08.jpg)

日志的作用有两个：当构建日志的数据块通过消息队列进来时，更新数据库对应行，然后推送它到Pusher用于实时的用户界面更新。

日志块以流的形式在同一个时间从不同的进程中进来，然后被一个进程处理。这个进程每秒最高可处理100个消息。

![架构图9](/image/The_Smallest_Distributed_System_09.jpg)

一般情况下这样处理日志流的方式也相当OK，但是这也意味着我们很难处理某些时刻突然增长的日志消息，因此这个唯一的进程对于我们系统的扩展会成为一个很大的障碍。

问题在于，进程是按照这些消息到达消息队列的先后顺序来进行处理的，而Travis CI中的所有事情都依赖于这些消息。

更新数据库里的一条日志流意味更新包含所有日志的一行数据。更新用户界面的日志当然意味着在DOM树上附加一个新的结点。

为了解决这个棘手的问题，我们需要改很多代码。

但是首先，我们需要理清楚什么才是一个更好的解决方案，好的解决方案应该是能够让我们很方便的扩展日志处理的部分。

我们决定让处理的顺序作为消息本身的一个属性，而不是隐含的依赖于它们被放进消息队列的顺序。

![架构图10](/image/The_Smallest_Distributed_System_10.jpg)

这个想法是受到Leslie Lamport于1978年发表的一篇论文[《Time, Clocks, and the Ordering of Events in a Distributed System》](http://research.microsoft.com/en-us/um/people/lamport/pubs/pubs.html#time-clocks)的启发。

在这篇论文中，Lamport描述了在分布式系统中，使用递增计数器来保留事件发生的顺序的方法。当一个消息被发送，发送者会在消息被接收者接收到之前增加计数器的值。

We could simplify on that idea, as one log chunk is always coming from just one sender. That process can take care of always incrementing the clock, making it easy to assemble a log from its chunks later on.

我们可以简化那个想法，因为在我们的场景中一个日志块只能来自一个发送者。进程只要不断增加计数器的值，就可以让之后的日志收集工作变得简单。

All that needs to be done is do sort the chunks by the clock.

剩下的工作就是根据计数器的值来对日志块进行排列了。








