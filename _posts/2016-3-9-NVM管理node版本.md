---
layout: post
title:  nvm管理node版本
date:   2016-3-9
author: 朱琛
category: ios
tags: []
---

##导语

<blockquote>node版本多，且又是需要同时有好几个版本的时候，使用NVM管理node版本非常方便</blockquote>


###安装
####通过脚本文件自动安装
终端中输入

$ curl https://raw.github.com/creationix/nvm/v0.4.0/install.sh | sh

或者

$ wget -qO- https://raw.github.com/creationix/nvm/v0.4.0/install.sh | sh

以上命令会将nvm仓库克隆到~/.nvm目录，并将启动脚本添加到shell配置文件中（~/.bash_profile、~/.zshrc 或~/.profile）

你还可以通过参数 NVM_SOURCE NVM_DIR NVM_PROFILE 进行自定义安装，比如curl ... | NVM_DIR=/usr/local/nvm sh

####通过源码手动安装

$ git clone https://github.com/creationix/nvm.git ~/.nvm 

$ cd ~/.nvm 

$ source ~/.nvm/nvm.sh # 将这一行加入到shell配置文件中，根据环境不同，可能是~/.bashrc, ~/.profile, 或 ~/.zshrc

###使用

####安装某版本的node

$ nvm install 0.10.26 #安装nodejs v0.10.26

$ nvm install 0.11 #安装nodejs v0.11.x最新版本


####删除某版本的node


$ nvm uninstall 0.10.26

$ nvm uninstall default


####在shell中切换使用已经安装的指定版本

$ nvm use 0.11

####你还可以在你的项目根目录中新建.nvmrc文件来存放node版本，然后在该目录运行


$ nvm use


####用指定版本运行some.js


$ nvm run 0.11.12 some.js



####查看已经安装的版本


$ nvm ls



####查看可以安装哪些版本


$ nvm ls-remote



####恢复使用系统安装的版本，撤销nvm使用的版本


$ nvm deactivate


####使用别名设置默认的版本


$ nvm alias default 0.10

$ nvm use default

####指定安装源

$ export NVM_NODEJS_ORG_MIRROR=http://nodejs.org/dist

$ nvm install 0.10

 或者
 
$ NVM_NODEJS_ORG_MIRROR=http://nodejs.org/dist nvm install 0.10









