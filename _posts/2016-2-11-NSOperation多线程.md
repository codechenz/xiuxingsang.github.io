---
layout: post
title:  NSOperation多线程
date:   2016-2-11
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>NSOperation是苹果在iOS4之后推出的一种多线程实现方式，本身是对GCD的一种封装实现，相对于GCD来说有可控性强，可加入操作依赖等优势。NSOperation是一个抽象的基类，可以为子类提供有用且线程安全的建立状态，优先级，依赖和取消等操作。下面我们来看看简单的一些实现。<blockquote>


###NSOperation类

NSOperation是一个抽象的任务类，本身不会实现多线程操作，可以创建一个继承NSOperation的子类TestOperation，在子类中重写main方法，如下图

![](http://ww4.sinaimg.cn/large/876dbe4fjw1f0wk274eufj20eg07pwfa.jpg)

然后初始化创建子类的对象，对象调用start方法，表示线程执行，release表示回收此线程。

![](http://ww2.sinaimg.cn/large/876dbe4fjw1f0wk30dqb1j20j30253z3.jpg)

以上两步是创建一个任务线程，并执行了该线程，但并未实现多线程。要想实现多线程，并对线程进行控制和操作，需要因为队列类，接下来让我们看看如何创建队列类。

###NSOperationQueue类
OC为我们提供了一个队列类，NSOperationQueue,初始化这个类。

* 通过setMaxConcurrentOperationCount方法来设置最大队列并发数，类似迅雷同时下载数。
* 初始化任务子类
* 通过addOperations方法将任务子类加入队列
* 执行完任务后需要对任务子类进行回收，并在所有任务完成后回收队列。

![](http://ww4.sinaimg.cn/large/876dbe4fjw1f0wk6pyob5j20ng0amgpc.jpg)

至此简单的NSOperation使用方法就结束了，需要了解更多多线程相关内容，那就关注我之后的博客吧。