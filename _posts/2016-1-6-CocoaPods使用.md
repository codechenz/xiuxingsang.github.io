---
layout: post
title:  "CocoaPods使用"
date:   2016-1-6
author: 朱琛
category: ios
tags: [ios]
---

## CocoaPods使用

### 导语

<blockquote>当你开发iOS应用时，会经常使用到很多第三方开源类库，比如JSONKit，AFNetWorking等等。可能某个类库又用到其他类库，所以要使用它，必须得另外下载其他类库，而其他类库又用到其他类库，“子子孙孙无穷尽也”，这也许是比较特殊的情况。总之小编的意思就是，手动一个个去下载所需类库十分麻烦。另外一种常见情况是，你项目中用到的类库有更新，你必须得重新下载新版本，重新加入到项目中，十分麻烦。如果能有什么工具能解决这些恼人的问题，那将“善莫大焉”。所以，你需要 CocoaPods。

CocoaPods应该是iOS最常用最有名的类库管理工具了，上述两个烦人的问题，通过cocoaPods，只需要一行命令就可以完全解决，当然前提是你必须正确设置它。重要的是，绝大部分有名的开源类库，都支持CocoaPods。所以，作为iOS程序员的我们，掌握CocoaPods的使用是必不可少的基本技能了。</blockquote>

### gem-注意修改ruby源

> `gem -v` //获取gem版本信息,查看当前版本是否为最新,否则下一步更新版本
> 
> `gem update --system` //可能需要管理员权限,sudo
> 
> 如果没有更新的话,尝试以下两个命令
> 
> `gem install rubygems-update` //可能需要管理员权限
> 
> `update_rubygems` //
> 
> `gem sources --remove https://rubygems.org/` //移除旧的ruby源
> 
> `gem sources -a https://ruby.taobao.org/` //替换为淘宝的镜像
> 
> `gem sources -l` //检查是否修改成功
> 
> `sudo gem install cocoapods` //安装cocoaPods,需要输入密码,为电脑的登录密码

引头文件问题:

`在Header路径里添加$(PODS_ROOT)  non-recursive改为recursive`

可以直接用""来引头文件


### 安装三方库文件

> `pod setup` //需要网络支持,非特殊情况避免使用
> 
> 将工程文件拖到终端里,获取当前工程路径
> 
> `touch Podfile` //创建Podfile文件, touch命令-新建
> 
> `open Podfile` //用Xcode打开 open-打开命令
> 
> 在podfile文件中添加
> 
> `pod search AFNetworking` //搜索三方库
> 
> `pod install --verbose --no-repo-update` 查看安装进度并且忽略没用的安装过程