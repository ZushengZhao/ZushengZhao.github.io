---
layout: post
title: "C++/MFC笔记_6"
date: 2018-11-10
categories: C++
tags: [C++, MFC, MSComm控件]
description: C++/MFC笔记_5
---

摘要：用C++/MFC编程实现串口通信，进而实现上位机和下位机的通信，为以后的控制做准备，先说一下怎么使用**CMSComm**控件，添加相关的变量。先不管以后的操作，VS2017配置CMSComm控件跟网上的很多教程都不太一样，这里进行说明。

---

## CMSComm控件的使用准备

### 添加CMSComm类

- 网上很多教程都是说直接先插入ActiveX控件，然后给控件添加变量，变量类型设置为CMSComm就行了。但是VS2017实际操作的话，添加CMSComm控件之后再为控件添加变量，变量选项没有CMSComm，就是说，要先**定义CMSComm类**。具体操作就是在**类向导**里面。

- 类向导——>添加类——>选择控件（Microsoft Communications Control, version 6.0）——>接口选择IMSComm——>自己命名，生成一个新类

如下图：

![]()

![]()

### 添加CMSComm控件

- 有了CMSComm类之后，我们**添加CMSComm控件**，方法是**插入ActiveX控件——>选择Microsoft Communications Control**
然后在软件窗体设计的界面就生成了一个电话一样的图标，这个图标在软件运行时会自动消失。

### 为CMSComm控件添加变量

- 右键CMSComm控件的图标，添加变量，变量类型选择刚才添加的类，比如我的是CMSComm2，变量类型就是CMSComm2然后确定。

做完了上述几步之后，这个类的关系就确定了，但是还有几个地方要自己改，不然编译会报错。

### 添加头文件

- 在对话框.cpp文件里面添加头文件**afxdisp.h**和**CMSComm2.h**。

```python
#include "afxdisp.h"
#include "CMSComm2.h"
```

### 修改控件变量

- 上述步骤添加控件变量，但是VS2017会出错，会产生下面的代码

```python
DDX_Control(pDX, IDC_MSCOMM2, DISPID(), mscomm);
```

这行代码编译会报错，我们要改一下
```python
DDX_Control(pDX, IDC_MSCOMM2, mscomm);
```

改完之后，同时我们要在对话框的.h文件里添加两个头文件，分别是**SComm2.h**和**afxwin.h**。
```python
#include "CMSComm2.h"
#include "afxwin.h"
```
添加完头文件之后，就可以编译了，编译成功，就可以进行之后的操作了。
