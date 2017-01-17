---
layout: post
title:  UITableView无数据和动画刷新
date:   2016-5-19
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>UITableView当无数据的时候，只显示一个白色的页面很不友好，所以可以写一个延展给tableview用，显示一个无数据的提示。</blockquote>


###动画刷新

func reloadDataAnimated(animated:Bool) {
        reloadData()
        if animated {
            let animation = CATransition()
            animation.type = kCATransitionFade
            animation.timingFunction = CAMediaTimingFunction(name: kCAMediaTimingFunctionEaseInEaseOut)
            animation.duration = 0.3
            layer.addAnimation(animation, forKey: "UITableViewReloadDataAnimationKey")

        }
    }

###无数据时延展方法

参数message为显示内容。

---

func tableViewDisplayWithMsg(message : String, rowCount : NSInteger) {
        
        if rowCount == 0 {
            let messageLabel = UILabel()
        
            messageLabel.text = message
            messageLabel.textColor = UIColor.lightGrayColor()
            messageLabel.textAlignment = NSTextAlignment.Center
            messageLabel.sizeToFit()
            self.backgroundView = messageLabel
            self.separatorStyle = UITableViewCellSeparatorStyle.None
        }else {
            self.backgroundView = nil
            self.separatorStyle = UITableViewCellSeparatorStyle.None
        }
      }