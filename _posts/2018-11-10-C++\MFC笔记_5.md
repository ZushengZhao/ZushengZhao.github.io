---
layout: post
title: "C++/MFC笔记_5"
date: 2018-11-10
categories: C++
tags: [C++, MFC, MSComm控件]
description: C++/MFC笔记_5
---

摘要：用C++/MFC编程实现串口通信，进而实现上位机和下位机的通信，为以后的控制做准备，先说一下怎么使用**CMSComm**控件，添加相关的变量。先不管以后的操作，VS2017配置CMSComm控件跟网上的很多教程都不太一样，这里进行说明。

---

## CMSComm控件的使用准备

### 添加CMSComm类

- 网上很多教程都是说直接先插入ActiveX控件，然后给控件添加变量，变量类型设置为CMSComm就行了。但是VS2017实际操作的话，添加CMSComm控件之后再为控件添加变量，变量选项没有CMSComm，就是说，要先**定义CMSComm类**
