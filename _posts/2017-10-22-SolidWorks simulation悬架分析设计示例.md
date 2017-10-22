---
layout: photo
title: SolidWorks悬架分析设计示例
date: 2017-10-22-22:00
description: 静态应力分析、优化设计、疲劳分析在悬架设计上面的应用。
---

摘要：参考SolidWorks simulation 2016基础教程和高级教程上的示例，自己做了一遍悬架的简单分析和优化，主要使用了simulation的静应力分析、优化设计和疲劳分析，其中静应力分析以四种载荷简单模拟汽车行驶中悬架的受力，然后通过设计算例可以优化悬架的尺寸，疲劳分析更贴近实际，用变载荷作为输入，分析疲劳点情况和零件寿命。

## 太长不看版

1. 静应力分析
 - a.设置零件的连接（销钉、弹簧等）和接触：
 - b.设置夹具；
 - c.施加载荷；
 - d.划分网格；
 - e.运算求解。
 注：静应力分析可以将载荷力链接到某个参数，然后在设计算例里面给该参数赋不同值，计算比较不同值下的应力和应变。
2. 优化设计（设计算例）
 - a.连接、接触、夹具和载荷同上；
 - b.选择一个设计变量；
 - c.新建设计算例，选择该变量，并赋予其变化规律；
 - d.得到变量取一系列值下的应力值大小，设计时选择合适变量值。
3. 疲劳分析
 - a.定义疲劳算例，添加事件；
 - b.修改材料参数；
 - c.设定结果位置；
 - d.设置算例属性；
 - e.运行算例，查看图解。
 
 示例来自《SolidWorks simulation 基础教程》和《SolidWorks simulation 高级教程》，示例文件我自己修改过了，文件在[这里](http://pan.baidu.com/s/1misYADy)，密码  ij5m。
 
 ## 正文
 
 # 1.静应力分析
 
 - 设置零件的连接（销钉、弹簧等）和接触
   销钉、弹簧和全局接触设置如下：
   销钉：
   
   ![](http://oxt33qs1f.bkt.clouddn.com/xiaoding1.png)
   
   弹簧：
   
   ![](http://oxt33qs1f.bkt.clouddn.com/tanhuang1.png)
   
 - 设置夹具
   添加铰链如下：
   
   ![](http://oxt33qs1f.bkt.clouddn.com/jiaolian1.png)
   
 - 施加载荷
  
  ![](http://oxt33qs1f.bkt.clouddn.com/zaihe1.png)
  
  各类夹具载荷等施加情况如图：
  
  ![](http://oxt33qs1f.bkt.clouddn.com/zong1.png)
  
 - 划分网格
 
  ![](http://oxt33qs1f.bkt.clouddn.com/wangge1.png)
  
 - 运行后得到应力和位移
 
  ![](http://oxt33qs1f.bkt.clouddn.com/jignyingli1.png)
  
 - 多载荷情况
  
  其实就是将载荷设置成变量，然后在算例里面赋予变量变化规律，计算出载荷取各个值的情况下的结果。
  载荷设置，链接到数值：
  
  ![](http://oxt33qs1f.bkt.clouddn.com/zaihe2.png)
  
  添加传感器，设置变量值：
  
  ![](http://oxt33qs1f.bkt.clouddn.com/chuanganqi.png)
  
  运行求解：
  
  ![](http://oxt33qs1f.bkt.clouddn.com/bianzaihejieguo.png)
  
  
 # 2.优化设计
 
 - 先解除载荷的链接，然后点击参数，选择一个设计参数（尺寸值）
   这里提一点，SW16建立的模型每个特征都有一个或者几个“主要值”，怎么去理解“主要值”的概念，我们以一个零件为例：
   这个零件在正常显示状态下会显示几个尺寸，鼠标点击其中一个尺寸，左侧边栏中出现主要值的名称和数值，直接在这里修改（或者在模型上点击该数值），零件尺寸即发生相应变化，不用找到相应的特征再右键编辑了。记住主要值的名称，它将作为一个变量名应用到之后的设计算例中。
   
   ![](http://oxt33qs1f.bkt.clouddn.com/zhuyaozhi1.png)
   
   ![](http://oxt33qs1f.bkt.clouddn.com/zhuyaozhi2.png)
 
 - 新建设计算例，以一个尺寸为变量运行分析
   
   添加传感器同上，然后变量这里选择尺寸D2，带步长范围，步长0.5.
   
   ![](http://oxt33qs1f.bkt.clouddn.com/zhuyaozhibianliang1.png)
   
   然后运行仿真，从结果看出，当D2从4.5到5的时候最大应力有显著减少，然后继续增大D2，应力和应变变化不明显。对设计来说，5mm应该是D2的一个合适的值。
   
   ![](http://oxt33qs1f.bkt.clouddn.com/zhuyaozhibianliang2.png)
   
   
 # 3.疲劳分析
 
 - 定义疲劳算例，添加事件
 
   定义疲劳算例，在选项下选择“可变高低幅历史数据”作为疲劳分析的类型。
   
   右击负载文件夹，选择“添加事件”，在“添加事件”窗口单击获取曲线，打开SAE suspension - modified.xls文件，直接Ctrl+S，Ctrl+C复制所有数据，然后在曲线数据里面点击一个单元格并Ctrl+V复制所有数据，然后得到载荷曲线。
   
   ![](http://oxt33qs1f.bkt.clouddn.com/shijian1.png)
   
   ![](http://oxt33qs1f.bkt.clouddn.com/shijian2.png)
   
 - 修改材料参数
  
   右键单击“零件”文件夹，选择“将疲劳数据应用到所有实体”，输入S-N曲线的数据点如图所示，设置应力比率和插值。
    
   ![](http://oxt33qs1f.bkt.clouddn.com/caoliaocanshu1.png)
   
 - 设定结果位置
 
   右击“结果选项”，选择“定义/编辑”，选择四个点，疲劳计算中选择 整个模型 。（对一个装配来说，疲劳损坏通常发生在不同材料的两个零件接触面）
   
   ![](http://oxt33qs1f.bkt.clouddn.com/jieguoweizhi1.png)
   
 - 设置算例属性
   
   右击“疲劳”，点击属性。如图设置算例属性：
   
   ![](http://oxt33qs1f.bkt.clouddn.com/shuxing1.png)
   
 - 运行并查看结果
   
   ![](http://oxt33qs1f.bkt.clouddn.com/jieguo.png)
   
   
   
   
 
<!-- more -->

**![Let us face reality, loyalty to an ideal.](http://oxt33qs1f.bkt.clouddn.com/Kurt%20Donald%20Cobain2.jpg)**

   

  
 
 
