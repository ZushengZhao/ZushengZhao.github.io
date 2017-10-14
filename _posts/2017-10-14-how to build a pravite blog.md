---
layout: photo
title: 如何搭建自己的私人博客
date: 2017-10-14 
description: 简单介绍如何搭建自己的私人博客
---

摘要：买了域名之后，自己跌跌撞撞尝试了许多搭建个人博客的方法，发现没有一个教程跟自己的建站过程一样。将自己用GitHub建站的过程写下来，为同样想建站的朋友提供一个思路，也正式开始自己的博客之旅。

## 前言

   一枚不懂编程和计算机的机械狗，只能用自己能理解的最简单的方法建站。用GitHub的原因有很多，体验一下GitHub的团队协作的思想，见识一下上面的大牛，而且GitHub是免费的，空间做一个静态网页足够了。当然，作为一个小白，买了域名以后不想再花钱租服务器了也是一个原因。

## 太长不看版

1. 注册域名。我用的是[Godaddy](http://www.godaddy.com/)；
2. 注册[GitHub](http://www.github.com/)，配置SSH Keys；
3. 将独立域名与 GitHub Pages 的空间绑定；
5. 用GitHub Pages建立博客（刚开始是直接用的Jekyll模板）；
6. 将独立域名与 GitHub Pages 的空间绑定；
7. 更新博客。

## 正文

  从注册域名到注册GitHub以及配置SSH Keys的具体操作请参考博主独立写生的教程——[如何搭建一个独立博客——简明GitHub Pages与jekyll教程](http://www.cnfeat.com/blog/2014/05/10/how-to-build-a-blog/)的教程。
[独立写生](http://www.cnfeat.com/)是我有建站想法之后查资料后接触到的令人印象最深的一个博主，他的一些文章，在自己建站之初给我做了很多的指引。我用GitHub建站最开始也是参考他的教程。

此处省略许多许多字......

  当你拥有了自己的域名、GitHub账户，下好了相应的软件，配置好了SSH Keys，并进行了域名解析，设置好了DNS，下面的教程从如何使用GitHub建立自己的博客开始。一定记得下面的教程是在完成了上述操作后才可以进行的！！！

# 1. 使用GitHub建立博客

- 创建pages仓库(repository)

  进入个人GitHub主页，点击new repository，Repository name为 你的用户名.github.io，例如我的GitHub用户名是zushengzhao,那么我的pages仓库名就是是zushengzhao.github.io。


![](http://oxt33qs1f.bkt.clouddn.com/1.jpg)


![](http://oxt33qs1f.bkt.clouddn.com/2.jpg)


  完成之后可以直接在settings里面点击Choose a theme，然后select a theme。
  

![](http://oxt33qs1f.bkt.clouddn.com/3.jpg)


![](http://oxt33qs1f.bkt.clouddn.com/4.jpg)


  选择完成后打开"你的用户名.github.io"确认一下确认一下网页是否发布，例如我的是[zushengzhao.github.io](zushengzhao.github.io)。
刚刚选择完主题后可能要稍微等一会才能刷新出网页。

  注意注意！！！choose a theme这步可以跳过，我们不用GitHub pages上仅有的几个英文模板，而是用[jekyll themes](http://jekyllthemes.org/)上的模板。我的博客用的 [Jacman](http://jekyllthemes.org/themes/jacman/) 就是在这个网站上找的模板，然后自己修改。下面会介绍如何下载并使用jekyll模板。

# 2. 将独立域名与 GitHub Pages 的空间绑定

- GitHub Pages 的设置

  进入你的github.io仓库，点击 create new file 新建文件，文件名为 CNAME ，在编辑框内输入你的域名。
  

![](http://oxt33qs1f.bkt.clouddn.com/5.jpg)


![](http://oxt33qs1f.bkt.clouddn.com/6.jpg)


  这一步完成后，你的域名应该已经导向 "你的用户名.github.io" 了。

  到这步大概应该理解了，用GitHub可以建立GitHub pages，就是一个静态网页，域名是“你的用户名.github.io”，添加CNAME文件就是域名映射，或者叫域名转向，将原来的 你的用户名.github.io 这个网址转到一个指定的域名上，因此你就可以通过你注册的域名访问你的个人博客了。

- 下面介绍如何使用下载和使用jekyll模板来搭建博客。

# 3. 用jekyll themes搭建博客

- 下载jekyll themes并上传到个人仓库

  下载模板可以直接点击[jekyll themes](http://jekyllthemes.org/)，选择其中的一个模板进行下载；也可以直接fork别人仓库的代码，或者直接进入别人仓库下载代码（.zip）。
  
  
 ![](http://oxt33qs1f.bkt.clouddn.com/8.png)
 
 
 ![](http://oxt33qs1f.bkt.clouddn.com/9.jpg)
 
 
  上传到个人仓库(upload)
  
 
 ![](http://oxt33qs1f.bkt.clouddn.com/10.jpg)
 
 
  同样的，当你把theme上传到自己的pages仓库后，修改文件CNAME，将里面的域名改为自己的域名，就可以了。
 
- 修改jekyll themes

  网页的主要配置文件是 _config.yml，可以根据里面的注释修改模板的基本信息。
  
  修改或者新增文章主要是_posts文件夹中的 md 文件，可以根据已有的文章文件仿照格式建立新文章。
  
  网页其他设置分散在不同的文件夹中，可以把每个文件都点开看一下，根据代码里面的关键词判断这个文件的作用。
  
 - 有关图床
  
  图床我用的 [七牛](http://www.qiniu.com/) ，也是看了推荐才用的，体验还可以，后期流量大了以后貌似会收费，目前暂时先用着。
  如何使用七牛，参考 [这里](http://jingyan.baidu.com/article/fd8044fac2a7df5031137aad.html)。
<!-- more -->

**![星星在夜空中闪亮  星空下我不停流浪](http://oxt33qs1f.bkt.clouddn.com/12.jpg)**

