---
layout: post
title: "C++/MFC笔记_5"
date: 2018-11-01
categories: C++
tags: [C++, Visual Studio， 网络编程]
description: C++网络编程，socket套接字的使用。
---

摘要：最近在学习网络编程，主要是通过网络传输视频图像，同时传输一些控制信号。

---

## socket编程

- sockets（套接字）编程有三种，分别是**流式套接字(SOCK_STREAM）**，**数据报套接字（SOCK_DGRAM）**，**原始套接字（SOCK_RAW）**。其中基于TCP的sockets编程采用的是流式套接字，基于UDP的是数据包套接字（无连接）。

因为我用到的是客户端编程，所以先介绍一下客户端的编程步骤。

- 客户端的编程步骤

1. 加载套接字库，创建套接字，主要用到WSAStartup（），socket（）；

2. 填写服务器的IP地址和端口；

3. 和服务器进行通信，用send（）传输，recv()接收；

4.关闭套接字closesocket（），关闭加载的套接字库WSACleanup（）。

- 下面是相关的代码，实现向地址为192.168.1.1，端口为2001，发送字符“F”。

```python
  WORD Send;   //WORD 字，两字节无符号整数
	WSADATA sendData;    //WSADATA ，结构体，存放Windows socket初始化信息
	Send = MAKEWORD(1, 1);   //调用1.1版本winsock
	WSAStartup(Send, &sendData);  //初始化Winsocket，1.指定要加载的Winsock版本，2.结构体指针
	//创建客户端SOCKET
	socket2 = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP); //AF_INET协议族，决定socket地址类型，ipv4地址，32位，与16位端口号；SOCK_STREAM TCP协议       
	tcpserver.sin_family = AF_INET;  //协议族
	tcpserver.sin_port = htons(2001);  //端口    htons转换为网络字节区 
	tcpserver.sin_addr.s_addr = inet_addr("192.168.1.1");  //IP地址  inet_addr将点分十进制转为ulong类型
	
	int nrt;
	
	nrt = connect(socket2, (SOCKADDR*)&tcpserver, sizeof(SOCKADDR));  //用来与服务器建立TCP连接（三次握手）,连接成功返回0，失败返回1
	if (nrt == SOCKET_ERROR)  
	{
		MessageBox("建立连接时出错");
		closesocket(socket2);
	}
	
	send(socket2, "F", strlen("F")+1, 0); //多发送一个字节

	MessageBox("指令发送");
	if (nrt == SOCKET_ERROR)
	{
		MessageBox("指令发送出错");
		closesocket(socket2);
	}
	closesocket(socket2);
	WSACleanup();
  ```
