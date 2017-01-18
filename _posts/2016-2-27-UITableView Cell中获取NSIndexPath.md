---
layout: post
title:  UITableView Cell中获取NSIndexPath
date:   2016-2-27
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>UITableView获取cell的row值（解决自定义cell里的button通过点击无法获得cell的indexpath的问题）</blockquote>


###在自定义cell中想获取cell是属于tableview的NSIndexPath
####1,可以使用协议方法将cell或者cell上的视图传出到VC中，
####2,然后使用 [view superview]取到cell。
####3,关键的一步，NSIndexPath *indexPath = [_myTableView indexPathForCell:cell];
####4,indexpath就是我们想获取的该cell的位置。 