---
title: 使用hexo构建博客，并部署在github pages
date: 2019-04-08 01:52:00
tags: 
 - tech 
 - blog 
 - hexo 
 - next
---

# 介绍
这个博客由hexo部署，简单方便，完全免费，有很多模板也可以直接使用，如果你希望专心于博客写作，推荐按照下面的步骤进行博客的搭建,如果你已经安装了git和nodejs,请直接跳到４，安装hexo　　　　
<!-- more -->
# 安装 git
git是一个代码版本管理的工具，由于hexo的代码保存在远程代码仓库github,我们需要进行使用git快速拷贝代码到本地，
官网的安装链接我放在下面了，也可以自己搜索，按照git官网的指引进行安装
https://git-scm.com/download/  
安装完成后在命令行(terminal)输入git --version出现版本信息，否则安装未成功
# 按转nodejs
hexo自动部署用到了nodejs，需要在本地电脑安装node和npm，直接在nodejs官网按照指引安装　　　　
https://nodejs.org/　　　　
安装完成后在命令行(terminal)输入node --version　和　npm -v出现版本信息，否则安装未成功　

# 安装hexo，初始化博客
在命令行输入
```
npm install hexo-cli -g
```
完成hexo安装，完成后同样使用hexo --version　会出现版本信息，否则安装失败，需要核对之前的步骤是否出现问题　  　
在https://github.com 建立账户，设置一个可以公共访问的邮箱，新建一个代码仓库(repository)，取名{你的github账户名字}.github.io(注意替换大括号以及其中的内容为你的github名字)，成功新建后，在命令行中进入本地想要创建博客文件夹的地方使用
```
hexo init {你的github账户名字}.github.io
```
这样你就新建了一个文件夹，在命令行中使用
```
cd {你的github账户名字}.github.io/
npm install
hexo server
```
输入完后，在本地浏览器打开localhost:4000可以看到hexo教程

# 部署在github上
在github仓库页面，点击clone or download 绿色按钮，选择clone with ssh，拷贝那串带有git@开头，.git结尾的信息，
在博客项目根目录下打开_config.yml,添加或修改(若已经存在delopy信息)deploy下的repo为刚才拷贝的信息，也可以手动填写　　　　
```
deploy:
  type: git
  repo: git@github.com:{你的github用户名}/{你的github用户名}.github.io.git
  branch: master
```
并修改URL
```
url: https://{你的github名字}.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
```
保存后，在博客项目根目录下可以运行，hexo generate,生成前端页面静态文件，然后使用hexo deploy自动部署到github pages上(此过程可能要求你输入github帐号密码，或者配置ssh,具体参考github　ssh key配置官方文档)，此时在github上的仓库里可以看到更新的代码，等待自动部署成功后(有时github pages会有一定时间延迟)，可以在https://{你的github名字}.github.io/访问你的主页　
# 创建博客
进入文件夹，使用
```
hexo new "我的第一篇博客"
```
创建博客，并在source/_posts/中修改博客内容

# 使用next主题
我的博客采用了next主题，当然有很多其他主题也可以选用，如果有兴趣，可以在博文下留言，我会根据留言情况更新next主题相关的教程

