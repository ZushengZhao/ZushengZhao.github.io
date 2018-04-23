---
layout: post
title: "MATLAB学习笔记_8：simulink中To Workspace的使用"
date: 2018-04-19
categories: MATLAB
tags: [MATLAB, 学习]
description: 用To Workspace模块将simulink仿真数据输出到Workspace窗口
---

摘要：用To Workspace模块将simulink仿真数据输出到Workspace窗口

---

- 刚开始用simulink做仿真的时候，有点把simulink跟MATLAB本体分开，输出波形也都是在simulink里直接看的，每次打开simulink模型都要重新运行一下仿真看看结果。后来想到了要把数据导入Workspace以便观察数据的最值以及绘图等操作，才开始使用To Workspace模块。（其实一开始就应该用的）

To Workspace模块使用其实很简单，就是输出格式需要注意一下，如图：

![](http://oxt33qs1f.bkt.clouddn.com/matlab_8_1.png)

几种输出格式的含义如下：

---

| 输出数据格式 | 含义 |
| --- | --- |
| structure | 结构体，包含三个字段:time、signals、blockName |
| structure with time | 与structure结构相同，不同之处在于 time 字段包含仿真时间点向量 |
| Array | 数组 |
| Timeseries | 将非总线信号另存为 [MATLAB timeseries](https://ww2.mathworks.cn/help/matlab/ref/timeseries-class.html) 对象，将总线信号另存为 MATLAB timeseries 对象的结构体 |

---
其中我之前有将数据以timeseries类型输出到workspace，以变量wax和wfx为例，该变量输出格式为timeseries，如果你要绘制该变量随时间变化的曲线，直接用```plot(wax)```即可，不必加变量t，```plot(t,wax)```是会报错的。如果想在一幅图上绘制几个timeseries变量，不能用```plot(t,wax,t,wfx)```，可以先绘制wax的图像，然后用```hold on```，再绘制wfx的图像。
```
plot(wax);
hold on;
plot(wfx);
```

### 参考资料：

1. MathWorks官网：[To Workspace](https://ww2.mathworks.cn/help/simulink/slref/toworkspace.html?s_tid=srchtitle)
2. MathWorks官网：[timeseries 类](https://ww2.mathworks.cn/help/matlab/ref/timeseries-class.html)
