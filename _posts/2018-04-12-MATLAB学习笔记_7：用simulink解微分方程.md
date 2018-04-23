---
layout: post
title: "MATLAB学习笔记_7：用simulink解微分方程"
date: 2018-04-012
categories: MATLAB
tags: [MATLAB, 学习]
description: simulink 微分方程
---

摘要：simulink搭建仿真系统，得到微分方程数值解。

---
- simulink里面有很多的模块库，常用模块库和各种专用模块库，用库中的模块搭建仿真系统进行仿真是simulink的优势，求微分方程的数值解是最基础的内容。比如有一个微分方程为：\\( dy = sin(x)，y(0)=-1 \\)，这是最简单的，答案也显而易见：\\( y = -cos(x) \\).下面在simulink里求解。

搭建仿真系统如图：

![](http://oxt33qs1f.bkt.clouddn.com/matlab_7_1.png)

- 其中输入为Sine Wave表示正弦波，Integrator为积分模块，Scope为示波器，用来显示输出波形。仿真时间为10s，Solver options采用默认值（simulink的Solver类型及使用跟MATLAB中类似）。

示波器波形如图：

![](http://oxt33qs1f.bkt.clouddn.com/matlab_7_2.png)

蓝色曲线为x的波形，黄色为y的波形。

- 如果是更复杂的系统，比如我在做的双旋弹7DOF外弹道仿真，动力学方程、运动学方程、力和力矩等等总共14个微分方程，还有很多随时间变化的参数，用simulink建模就比较直观方便，可以随时监控每一个变量的波形，如果出现问题更容易找到问题的来源。而且simulink的专用模块库功能很强大，我用到了一点点航空模块库（Aerospace Blockset），以后再总结。
- 这是一个最简单的simulink解微分方程的例子。
