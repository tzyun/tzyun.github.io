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
<!--more-->
## 准备
Git客户端安装，以及相关Git操作，这部分请自行百度。
nodeJs，主要是用作本地服务器可以预览效果。
Hexo，是一个快速、简洁且高效的博客框架。还有一种Jekyll，网上说Hexo速度快，都试了一下，感觉Hexo相对美观和简单点。
yilia，一个界面的模板而已，可以自行选择喜欢的，这里用的是** https://github.com/voidking/hexo-theme-yilia.git **	。

## Github配置
Git客户端配置，Github账号申请， SSH Key配置。
创建一个仓库，命名为username.github.io（username 是你的账号名)
	
![创建仓库](/img/github_create_blog/create_repo.png "创建仓库")
	
建立两个branch，master用于发布的网页，另外一个blog用于Hexo网页文件，手动管理和编辑的是blog分支，在该repo的setting设置GitHub Pages中为master branch。

## Hexo环境配置
安装[nodejs](https://nodejs.org/en/)
将上面创建的repo clone到本地，打开Git Bash。
``` bash
#Hexo 的安装
$ npm install hexo-cli -g
#查看版本，确认是否安装成功
$ hexo -version 
#建站
$ hexo init
#依次输入git --version,node -v,npm -v,hexo version，依次检测 Git node npm 以及 hexo 的版本
$ git --version,node -v,npm -v,hexo version
#生成静态页面（markdown文件转化为html文件）
$ hexo generate
#网站预览（默认的主题风格landscape, http://localhost:4000/)
$ hexo server
```

### Hexo常见命令
常见命令
``` bash
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
缩写
``` bash
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```
组合
``` bash
hexo s -g #生成并本地预览
hexo d -g #生成并上传
```


## yilia模板
模板下载,hexo的模板有很多，可以自己选择一款
``` bash
#进入themes目录，下载yilia主题
git clone https://github.com/voidking/hexo-theme-yilia.git yilia
```
配置文件修改， 主题的优化参考** https://www.voidking.com/2015/05/31/deve-hexo-theme-optimize/ **
``` bash
#进入usename.github.io下面的_config.yml修改，主要是下面这一条
theme: yilia
```
现在可以在本都预览到yilia样式的博客了。

## 发布到github
首先是将该项目同步到github的blog分支，普通的git操作。
``` bash
git pull origin blog
git add .
git commit -am " "
git push origin blog
```
然后是将博客生成静态页面deploy到github的master分支。
再次之前，首先配置_config.yml中有关deploy的部分，修改为如下所示。
``` bash
deploy:
  type: git
  #对应仓库的SSH地址（可以在GitHub对应的仓库中复制）
  repo: git@github.com:usename/usename.github.io.git 
  #（分支：User Pages为master，Project Pages为blog分支）
  branch: master
```
配置完成后保存，然后鼠标右键单击你的项目文件夹开启git bash，输入npm install hexo-deployer-git --save安装相关插件。
用hexo deploy命令发布生成后的HTML代码到 master 分支上。
``` bash
hexo generate
hexo deploy
#或者用组合指令
hexo d -g
```
日常编写的博客在source下面的_posts文件夹下面，用markdown格式编写，然后预览后没问题就上传，项目上传到blog分支，静态网页在master分支。

## 参考文献

[hexo主题优化](https://www.voidking.com/2015/05/31/deve-hexo-theme-optimize/)

[GitHub+Hexo搭建博客](https://www.jianshu.com/p/7b5702d3f072)

[github+hexo 搭建属于自己的博客网站](https://www.jianshu.com/p/e6662ca7e283)


