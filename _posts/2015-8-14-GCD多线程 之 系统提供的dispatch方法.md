de---
layout: post
title:  GCD多线程 之 系统提供的dispatch方法
date:   2015-8-14
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>GCD全名为Grand Central Dispatch，字面意思重要中枢派发机制，是一种多线程编程的解决方法，在IOS4之后推出，由于其与block的搭配使用，极大的简化了之前多线程编程方法，且集中了同功能代码，提高可读性。可以应用一些简便的多线程编程需求。</blockquote>

###后台执行

![](http://ww2.sinaimg.cn/large/876dbe4fjw1f0wktp8nv7j20gw02jq3b.jpg)

###主线程执行

![](http://ww3.sinaimg.cn/large/876dbe4fjw1f0wkx3nw8xj20ew02lmxj.jpg)

###只执行一次
常用于实现单例模式，例如音乐播放控制类

![](http://ww2.sinaimg.cn/large/876dbe4fjw1f0wkzcfxenj20bk03fdga.jpg)

###延迟执行

![](http://ww1.sinaimg.cn/large/876dbe4fjw1f0wl49w4twj20os04iq4b.jpg)

###自定义进程
dispatch_queue_t 也可以自己定义，如要要自定义 queue，可以用 dispatch_queue_create 方法，示例如下

![](http://ww1.sinaimg.cn/large/876dbe4fjw1f0wma644pcj20hl02zq3k.jpg)

###多进程并发

另外，GCD 还有一些高级用法，例如让后台 2 个线程并行执行，然后等 2 个线程都结束后，再汇总执行结果。这个可以用 dispatch_group, dispatch_group_async 和 dispatch_group_notify 来实现，示例如下：

![](http://ww3.sinaimg.cn/large/876dbe4fjw1f0wmbc4hz8j20f805agmx.jpg)



