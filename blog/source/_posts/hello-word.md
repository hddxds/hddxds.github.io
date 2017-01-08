---
title: Hello Word! 我是怎么建立一个博客的
date: 2017-01-08 16:37:15
categories: hexo
tags:
    - hexo
    - github
---
## 前言
你好我的博客，终于建成了。因为一个大考试很久没有学习新技术了，今天小折腾一下完成了这个博客，也算是满足了一直以来小小的愿望。第一篇不知道写什么好，建这个博客也算是经历了一些很麻烦的事情，索性写一些在建博时候遇到的问题和一些心路历程。网上的资料很多所以我在这里仅仅列出自己建博时的参考资料，希望能够帮助到一些人(其实我自己还是萌新^^)。<!--more-->

## 开始建立
### 失败的第一次，使用jekyll搭建博客
在我构建自己博客的过程中，参考了很多***[简书](http://www.jianshu.com/)***上边的文章。最开始使用jekyll尝试建立博客，这是我最开始的参考文章。  

> **[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门 —— 阮一峰](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)** 

我通过他搞明白了github-pages是个什么东西，并且发现了一个更好的教程。

> **[一步步在GitHub上创建博客主页 全系列 —— pchou](http://www.pchou.info/ssgithubPage/2013-01-03-build-github-blog-page-01.html)**

但是我的Windows安装的Ruby始终有问题,安装好了jekyll后开启本地调试服务器一直有问题，在我爆炸了准备转移到Ubuntu上开发的时候，我发现了hexo。
### 改变思路，使用hexo搭建博客
Hexo 是一个简单地、轻量地、基于Node的一个静态博客框架，可以方便的生成静态网页托管在github和Heroku上，引用Hexo作者 *[@tommy351](https://github.com/hexojs/hexo)* 的话：

>*快速、简单且功能强大的 Node.js 博客框架。A fast, simple & powerful blog framework, powered by Node.js.*

在使用hexo搭建博客的时候，下面这篇文章帮助了我，让我很快的上手并且成功安装了hexo到本地，并且非常方便的开始了本地的调试。

> **[hexo你的博客 —— ibruce](http://ibruce.info/2013/11/22/hexo-your-blog/)**

## 将博客部署到github
在很久之前，我们通过***[廖雪峰](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)***的网站学习git的基本操作。但是结合github后我始终不太理解github多人协作的流程，于是我通过***[一个慕课网的视频教程](http://www.imooc.com/learn/390)***彻底理解了github结合本地的操作并且理解了github for windows的一些操作(我有些强迫症，虽然会使用命令行，但是老觉得既然有个客户端，那么就一定要用客户端测试一遍同样的功能)。

### 备份hexo到github远程仓库
在我通过上边的一系列教程将我的博客部署到github上了以后，我发现hexo不像jekyll一样，每次将本地的文件直接传到github上边，没有备份之忧。hexo是直接通过`$ hexo generate -deploy`命令直接将编译好的文件同步到github的远程仓库的目标分支上，所以当我们更换电脑或者丢失文件之后，直接将github相应仓库的项目clone到电脑上并不是完整的hexo文件。在查找资料后，我找到了一个可靠的文章。

> **[使用hexo，如果换了电脑怎么更新博客？ - 回答作者: CrazyMilk ](http://zhihu.com/question/21193762/answer/79109280)**

这个文章的思路是十分方便干净的，但是在备份中我遇到了一些小问题。首先，在你本地clone下来的空项目中直接运行`$ hexo init`命令时，会把本地仓库中的`.git`文件删除，导致同步到远程备份分支失败。我的解决办法是在本地仓库中新建一个任意名字的文件夹(名字是blog)，在这个文件夹中运行`$ hexo init`命令，再同步到远程hexo备份分支。问题完美解决。另外有一个问题上边的文章没有提到，我们可以在git项目的`.gitignore`文件中添加如下忽略文件。
```
./blog/deploy*/
./blog/public/
./blog/node_modules/
```
这些文件都是每次hexo编译时生成的，node_modules也是可以后来通过`$ npm install`命令生成的。用不着每次上传。

## 我使用的hexo主题
在hexo我终于找到了喜欢的主题，参考了知乎的一个回答，这个回答下边有很多优秀的主题.
> **[有哪些好看的 Hexo 主题？ - 回答作者: 家顺张 ](http://zhihu.com/question/24422335/answer/46357100)**

我挑选了风格简洁的***[NexT主题](https://github.com/iissnan/hexo-theme-next)***，以下是NexT主题的***[帮助文档](http://theme-next.iissnan.com/getting-started.html)***。这个主题集合了很多插件，在他的帮助文档中都有。使用十分简单。但是，在使用NexT主题中出现了一个小问题，我在备份时，在next主题的文件夹中存在一个`.git`文件导致不能同步，删除它就好。不过我还是更喜欢`Mist`这个风格，可是在建站后发现我有个同学也用了这个模板的Mist风格，所以我就变成了`Pisces`风格，要不太傻了。他的博客:[Randy's Notes](http://pengzhendong.cn/)

## Markdown标记语言的学习
在建立博客前学习使用EverNote的时候学习了如何使用Markdown，下边是一个非常实用的网站，通过它可以十分方便的学习Markdown。
> **[欢迎使用马克飞象](https://maxiang.io/#fn:demo)**

## 使用七牛云管理资源
我使用七牛云托管博客的资源，图片之类的。这个文章帮助了我。
> **[Hexo文章图片存储选七牛(当然支持MD都可以) —— Codeagles](http://www.jianshu.com/p/ec2c8acf63cd)**

## 尾声
好了，就把它作为我的第一篇博客吧，写了很长时间，希望能够帮助到别人，这个博客还有很多的东西需要完善，以后再写了，我是个程序员，希望这个博客能够督促我更好更稳定的学习技术，我会尽量定时将我的技术感悟写出来，分享在这里，谢谢观看。








