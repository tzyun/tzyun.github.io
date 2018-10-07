---
title: Github+Hexo+yilia快速搭建博客
toc: true
categories: 
  - 其他
tags:
  - github
  - hexo
---
GitHub是一个面向开源及私有软件项目的托管平台，也是一个分布式版本控制系统，详情见百度百科。
Github Pages则是github上的一项功能，可以放置网页文件到指定文件夹，然后给你一个专属域名用于展示一些项目，但现在大多用来开发制作个人博客网站。
接下来就一步步按照我曾经的步骤来搭建个人博客。
## 准备
	Git客户端安装，以及相关Git操作，这部分请自行百度
	nodeJs，主要是用作本地服务器可以预览效果
	Hexo，是一个快速、简洁且高效的博客框架。还有一种Jekyll，网上说Hexo速度快，都试了一下，感觉Hexo相对美观和简单点。
	yilia，一个界面的模板而已，可以自行选择喜欢的，这里用的是** https://github.com/voidking/hexo-theme-yilia.git **	
---

## Github配置
	Git客户端配置，Github账号申请， SSH Key配置。
	创建一个仓库，命名为username.github.io（username 是你的账号名)
	
	![创建仓库](img/github博客创建/create_repo.png)
	
	建立两个branch，master用于发布的网页，另外一个blog用于Hexo网页文件，手动管理和编辑的是blog分支。
	
``` bash
$ hexo new "My New Post"
```
<!--more-->
More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
