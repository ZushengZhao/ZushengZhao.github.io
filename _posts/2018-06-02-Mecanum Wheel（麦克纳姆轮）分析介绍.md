---
layout: post
title: "麦克纳姆轮（Mecanum Wheel）分析介绍"
date: 2018-06-02
categories: 机械
tags: [Mecanum Wheel, Simulink]
description: 介绍麦克纳姆轮的原理，对其进行运动学分析，利用MATLAB/simulink 建模仿真得到不同运动条件下四轮转速的关系。
---

摘要：介绍麦克纳姆轮的原理，对其进行运动学分析，利用MATLAB/simulink 建模仿真得到不同运动条件下四个轮字转速的关系。
---

-[麦克纳姆轮（Mecanum Wheel）](https://baike.baidu.com/item/%E9%BA%A6%E5%85%8B%E7%BA%B3%E5%A7%86%E8%BD%AE/3827219?fr=aladdin)是做[RoboMaster](https://www.robomaster.com/zh-CN)机器人大赛的时候接触到的，当时就觉得这种轮子很神奇，因为主办方有一款麦轮出售，我们一直也是用的官方的麦轮，对其没有进行深入的了解。在2018RoboMaster中部赛区的比赛上看到了有的学校的麦轮底盘平移的时候可以同时自转，对这个比较感兴趣，就了解了一些麦轮的知识。然后在工作室跟去年秋招的新人进行了一次培训交流，这里再进行一下总结，很多会用到培训的PPT。

# 基本知识及原理简介：

![](http://oxt33qs1f.bkt.clouddn.com/MW4.JPG)

-底盘布置就是这样的（俯视图）
![](http://oxt33qs1f.bkt.clouddn.com/MW_MW.png)

-一些图片
![](http://oxt33qs1f.bkt.clouddn.com/MW5.JPG)

优缺点：
![](http://oxt33qs1f.bkt.clouddn.com/MW6.JPG)

优缺点其实也比较好理解，结构复杂一眼就能看出来，每次与地面接触的只有一两个辊子，小辊子受力比较大，因此承载能力有限。另外底盘的运动是四个轮子运动的叠加，因为单个轮子的摩擦力是斜着的，如果因为地面起伏造成一个轮子悬空，底盘的运动就会被破坏。

# 车体运动学分析

-运动学分析主要基于以下两个图，一个是底盘的俯视图，一个是运动简图。运动简图选取的是地面，因此辊子的方向与俯视图中相反。

![](http://oxt33qs1f.bkt.clouddn.com/MW8.JPG)

其实对这个速度的分解我个人是这样理解的，如果是正常的车轮，只有一个方向的速度，速度大小等于轮子转速乘以轮子半径，麦轮因为有小辊子，小辊子可以独立转动，所以叠加小辊子的速度，就是下面的方程了。

![](http://oxt33qs1f.bkt.clouddn.com/MW9.JPG)

解方程，得

![](http://oxt33qs1f.bkt.clouddn.com/MW10.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW11.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW12.JPG)

简单总结一下：

![](http://oxt33qs1f.bkt.clouddn.com/MW13.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW15.JPG)

-接下来分析一下，如果需要让底盘边平移的同时，边自转，怎么计算四个轮子的转速。这里其实就一个关键点，就是引入固连坐标系，然后固连坐标系上不变的速度方向，放到车体坐标系上，得到一个新的速度角，然后用这个速度角计算四个轮子的转速。

![](http://oxt33qs1f.bkt.clouddn.com/MW16.JPG)

# 车体运动仿真

-这里就根据以上分析结果，用simulink进行运动仿真，仿真结果如下：

![](http://oxt33qs1f.bkt.clouddn.com/MW18.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW19.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW20.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW21.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW22.JPG)

![](http://oxt33qs1f.bkt.clouddn.com/MW23.JPG)











