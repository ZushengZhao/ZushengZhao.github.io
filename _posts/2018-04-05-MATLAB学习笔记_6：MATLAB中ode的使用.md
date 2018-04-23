---
layout: post
title: "MATLAB学习笔记_6：MATLAB中ode的使用"
date: 2018-04-05
categories: MATLAB
tags: [MATLAB, 学习]
description: ode
---

摘要：MATLAB中ode的使用，刚性方程的解释。

- MATLAB中ode求解器用来解微分方程（组），一般情况下ode45可以解决大多数问题，可以作为首选求解器。但是对于刚性方程来说，ode45并不适用，MATLAB中有专门的针对刚性方程的求解器如ode23s,ode23t等。各个求解器的基本情况如下表：

---

| 求解器 | 问题类型 | 精度 | 原理 | 何时使用 |
| --- | --- | --- | --- | --- |
| ode45 | 非刚性 | 中 | 使用Runge-Kutta的四-五阶算法,用4阶方法提供候选解，5阶方法控制误差 | 多数情况下的首选 |
| ode23 | 非刚性 | 低 | 使用Runge-Kutta的二-三阶算法 | 容差较宽松或刚性适中时可能比ode45高效 |
| ode113 | 非刚性 | 低到高 | 变阶次Adams-Bashforth-Moulton PECE算法 | 容差严格或者具有大量计算开销的时候比ode45高效 |
| ode15s | 刚性 | 低到中 | 使用可变阶次的数值微分（NDFs）算法 | 当ode45解算失败，方程可能面临刚性问题，或者微分代数方程时，使用ode15s |
| ode23s | 刚性 | 低 | 低阶方法，使用修正的Rosenbrock公式 | 对于容差较宽松问题和刚性问题，效率比ode15s高 |
| ode23t | 刚性 | 低 | 使用自由内插法的梯形法则 | 解刚度适中的问题，和微分代数方程 |
| ode23tb | 刚性 | 低 | 低阶方法，使用TR-BDF2方法，即Runge-Kutta公式，第一级采用梯形法则，第二级采用GEAR法 | 类似ode23s，容差较宽松时更高效 |

--- 
- 而所谓**刚性方程**，就是方程中存在两个（或多个）尺度，尺度之间相差悬殊，在计算中很难兼顾。专业一点解释就是方程组的Jacobian矩阵特征值的最大和最小值相差十分悬殊。表现为方程的解，其中一些变化缓慢，另一些变化快，且相差悬殊，这类方程称为刚性方程，又称**Stiff方程**。

### 参考资料：

1. MathWorks官网：[选择 ODE 求解器](https://ww2.mathworks.cn/help/matlab/math/choose-an-ode-solver.html)
2. mec_zhang的博客：[ Matlab之ODE](https://blog.csdn.net/mec_zhang/article/details/71038481)
3. 观测者的博客：[MATLAB中ODE的使用](http://blog.sina.com.cn/s/blog_6b20fa3d0101ne1z.html)
4. 百度百科：[ode45](https://baike.baidu.com/item/ode45/6674723?fr=aladdin)
