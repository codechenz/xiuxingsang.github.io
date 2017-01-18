---
layout: post
title:  Swift 代码关联UIView XIB view基类
date:   2016-2-27
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>swift为nib写一个view的基类</blockquote>


 var view : UIView?

    //初始化方法
    func initFromXib(){
        //获取Xib文件名字
        let xibName = NSStringFromClass(self.classForCoder)
        let xibClassName = xibName.characters.split{$0 == "."}.map(String.init).last
        //使用Xib初始化一个View
        let view = NSBundle.mainBundle().loadNibNamed(xibClassName, owner: self, options: nil).first as! UIView
        view.frame = self.bounds
        view.translatesAutoresizingMaskIntoConstraints = true
        view.autoresizingMask = [.FlexibleWidth,.FlexibleHeight]
        self.addSubview(view)
        self.view = view
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        initFromXib()
    }

    required init(coder aDecoder: NSCoder) {
        super.init(coder:aDecoder)!
        initFromXib()
    }