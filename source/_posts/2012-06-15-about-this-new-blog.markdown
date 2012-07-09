---
layout: post
title: "About this new blog"
date: 2012-06-15 22:14
comments: true
categories: 
---
前博客时代
-----------

以前曾经试过很多博客，比如wordpress.com, livejournal，轻博客。曾经在很短的一段时间内还自己买域名搭过一个wordpress。但一直没有觉得很合适的解决方案。

一般都是遇到这些问题

* 国内的博客访问速度可以，但是定制性一般都比较差，界面也没有特别让人满意的。更别说什么支持粘贴代码的插件了
* 国外的博客服务，常见的基本上逃不过被墙的危险，不被墙的访问速度也基本处于可用的边缘
* 自己搭的博客在维护上比较麻烦，对于我这样把博客半做博客，半做笔记整理的用户，实在很难坚持维护下去

最近正好迷上了markdown的语法。最早是在sublime里面用，被markdown-preview的效果很是惊艳了一下，后来发现emacs, vim都早已有广泛支持。于是觉得拿来写最近做的人脸项目的文档正好合适。

git和github也是用了有一段时间的东西了，github在国内一直能顺畅的访问，让人很是喜欢。

发现octopress
------------
前几天看deep learning的时候看到了[echen的blog](http://blog.echen.me/)，研究了一下发现是host在github上的，联想到最近[pluskid](http://blog.pluskid.org)的博客也在迁移，用的也是一种静态博客的技术。好奇心及不折腾不舒服斯基的精神驱动下，觉得研究一下。没想到，还发现了其中的许多乐趣。


[echen的blog](http://blog.echen.me/)用的是[octopress](https://github.com/imathis/octopress)这个工具。octopress号称是为hacker而生的blog。当然没那么夸张啦。只是它用的一些东西是程序员日常工作中很熟悉的，因此程序猿用起来会觉得非常顺手~。

octopress用到了这些东西

* markdown的语法
* git和github
* ruby
* jekyll这个静态html生成工具

使用octopress的好处

* 版本管理
* 可以选择自己喜欢的编辑器
* 用markdown语法，简洁快速

坏处估计是强烈依赖于github的服务，以及对新人的要求有点高了。

octopress据说是jekyll的傻瓜版。如果以上几个东西你都很熟悉，那用起来应该会很顺手，如果像我只会前两样，基本的使用应该也挺顺畅。

octopress的使用
-------------
这里顺带列一下装octopress要用到的几个常用的链接

* [Initial setup](http://octopress.org/docs/setup) ruby的安装之类的东西，如果像我一样是在linux的包管理器里装的ruby，要记得装对应的ruby-dev包
* [Basic Configuration](http://octopress.org/docs/configuring) 基本的配置文件说明
* [Deploying Octopress](http://octopress.org/docs/deploying) 介绍如何把Octopress发布到github，我没仔细看说明就开始折腾，这里浪费了好一会
* [Blogging Basics](http://octopress.org/docs/blogging) 如何写博客

如果要修改默认的主题，可以参考github上的wiki页面[List of themes](https://github.com/imathis/octopress/wiki/List-Of-Octopress-Themes)。

octopress用的是Github提供的page服务，如果有兴趣，最后看看Github Pages的[介绍](https://help.github.com/categories/20/articles)

所以总结一下，目前这个博客就是用github+octopress做的，每次用emacs写完markdown的文件后，在shell里面rake generate, rake push一下，就更新到博客里了。

rake是ruby中类似makefile的工具，通过一个rakefile文件，就可以把博客维护要用到的一些命令都整合在一起，非常贴心。
rake的命令可以直接tab补全出来，我目前会用的只有

* rake setup_git_pages  
格式是git@github.com:qiuwch/qiuwch.github.com.git, 初始化git pages
* rake generate  
生成Jekelly style files
from source generate pages
* rake deploy  
This seems not working well
* rake push  
Push generated pages to github
* rake gen_deploy
* rake new_post
* rake preview 这个可以动态更新，很方便

修改和更新的方法

* 修改post下的markdown原文件
* rake generate
* rake push

目前觉得还不顺手的地方有几个

* 模板中的字体大小不怎么协调，正文好像太小了
* 在emacs里发布不怎么方便，不过有preview功能，问题不大
有时间再继续折腾，做完ComputerVision的实验报告，该做些正事了。
