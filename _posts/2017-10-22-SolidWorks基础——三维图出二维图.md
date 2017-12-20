---
layout: photo
title: SolidWorks基础——三维图出二维图
date: 2017-10-22 
description: 三维图出二维图的指南
---

摘要： SolidWorks作为一个强大的三维建模软件，使用其三维建模的功能十分方便，但是三维图出二维图的时候，会有各种不友好的情况发生，有些该隐藏的线没有隐藏，标题栏不好设置，还有各种字体尺寸样式什么的都要改。。。这个时候，用CAXA做工程图的便利就体现出来了，CAXA是一款国标友好的软件，用其进行二维图的修改很方便。当然，SolidWorks出二维图有其特色，就是可以直接在工程图显示隐藏边线、螺纹线、中心线，做局部视图和剖视也很方便。现在基本思路就是用SW制作工程图，然后用CAXA修改。


## 太长不看版

1. 用SW从零件图制作工程图，选择图纸，设置比例和投影类型；
2. 视图选择：局部视图、剖视图、轴测图等；
3. 设置显示形式，添加中心线等；
4. 另存为dwg格式，设置映射将SW图层与dwg图层对应上。
5. 用CAXA修改dwg文件至符合标准。

## 正文

# SW生成工程图，设置比例和投影类型

如图，右击“图纸一”，选择属性，更改比例（一般为1:1，添加尺寸的时候比较方便），投影类型选为“第一视角”（这样符合国标三视图的投影要求）。
![](http://oxt33qs1f.bkt.clouddn.com/shuxing_.png)

# 视图选择：根据需要选择局部视图、剖视图等

根据零件表达需要设置视图，SW做剖视图的功能很方便。


# 设置显示形式，添加中心线等

显示形式主要考虑到不同显示形式对不可见边线的处理不同，另外有螺纹的地方也要注意装饰螺纹线的显示。

![](http://oxt33qs1f.bkt.clouddn.com/shituxuanze_.png)

没什么图好贴了，贴一张我之前做课程设计时候做的工程图吧。。。
![](http://oxt33qs1f.bkt.clouddn.com/shitu.png)

# 另存为DWG格式

如图，另存为“DWG”文件，然后点击选项，设置里面的映射，也可以直接加载[映射文件](https://pan.baidu.com/s/1kUFOwj9)。
映射的主要目的就是将SW工程图里面的图层对应到DWG文件里面，然后用CAXA或者AutoCAD编辑DWG文件的时候就会看到图层那里除了默认的几个图层外会有从SW映射过去的图层，比如SW里面的可见边线。

![](http://oxt33qs1f.bkt.clouddn.com/xuanxiang.png)

![](http://oxt33qs1f.bkt.clouddn.com/yingshe.png)

![](http://oxt33qs1f.bkt.clouddn.com/yingshe2.png)

![](http://oxt33qs1f.bkt.clouddn.com/yingshe3.png)

# 修改DWG文件至符合标准
参照制图标准修改工程图。

随便贴一张课设的图，用CAXA改好的。

![](http://oxt33qs1f.bkt.clouddn.com/dwg.png)

结束~


 
 
<!-- more -->

**![Let us face reality, loyalty to an ideal.](http://oxt33qs1f.bkt.clouddn.com/Kurt%20Donald%20Cobain2.jpg)**
