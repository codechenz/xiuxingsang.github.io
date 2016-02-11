---
layout: post
title:  "CAGradientLayer实现渐变色效果"
date:   2016-1-19
author: 朱琛
category: ios
tags: [ios]
---

##CAGradientLayer实现渐变色效果

###导语

<blockquote>开发中如果要实现渐变色效果时，如下图，在imageview上层铺一个覆盖层，覆盖层由下方的黑色半透渐变至透明。可以使用 CAGradientLayer 类来实现，具体方法如下</blockquote>

![pic1](http://ww1.sinaimg.cn/large/876dbe4fjw1f04sthej05j20az09xabc.jpg)



###具体实现

####一.首先看一下iOS中的坐标系统

![pic2](http://ww4.sinaimg.cn/large/876dbe4fjw1f04t3r1bxqj208i06rt8r.jpg)

####二.初始化并设位置

CAGradientLayer *colorLayer = [CAGradientLayer layer];

colorLayer.frame  = self.view.bounds;//为其设位置

####三.因为CAGradLayer是layer层的类，所以要添加到view的layer层中
 [self.view.layer addSublayer:colorLayer];
 
####四.颜色分配，需要注意的是颜色不能使用UIColor，需要转换为CGColor，并在颜色前加(__bridge id)修饰

colorLayer.colors =  @[(__bridge id)[UIColor blackColor].CGColor,(__bridge id)[UIColor clearColor].CGColor];
    
####五.颜色分割线，可不加
 
 colorLayer.locations  = @[@(0.25), @(0.5), @(0.75)];

####六.起始点，layer层是一个二维坐标系第四象限，原点为（0，0）位于视图的左上角；
colorLayer.startPoint = CGPointMake(0, 1);

####七.结束点

colorLayer.endPoint   = CGPointMake(0, 0)
    