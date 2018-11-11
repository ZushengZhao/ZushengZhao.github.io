---
layout: post
title: "C++/MFC笔记_7"
date: 2018-11-10
categories: C++
tags: [C++, MFC, MSComm控件]
description: C++/MFC笔记_6
---

摘要：用C++/MFC编程实现串口通信，添加了MSComm控件后，介绍一下控件的基本操作，实现串口的收发数据。

---

## 打开/关闭串口及串口的初始化

```python
void CMSCommDemoDlg::OnBnClickedButton1()
{
  if (!m_comm.get_PortOpen())
    {

		CString baud;
		GetDlgItemText(IDC_CMB_BAUD, baud);  //通过ComboEditor控件选择串口波特率，将值传给baud
		CString baudPort = baud + _T(",n,8,1");  //波特率，无校验，8个数据位，1个停止位
		m_comm.put_CommPort(m_cmbCom.GetCurSel() + 1);  //选择com口
		m_comm.put_InBufferSize(1024); //   put__InBufferSize(1024); //设置输入缓冲区的大小，Bytes
		m_comm.put_OutBufferSize(1024);   // put__OutBufferSize(512); //设置输入缓冲区的大小，Bytes// 
		m_comm.put_PortOpen(TRUE);//  SetPortOpen(TRUE);  打开串口
		m_comm.put_InputMode(1);  //  SetInputMode(1); //设置输入方式为二进制方式
		m_comm.put_Settings(baudPort);    //  SetSettings("9600,n,8,1"); //设置波特率等参数
		m_comm.put_RThreshold(1); //SetRThreshold(1); //为1表示有一个字符引发一个事件，每当接收缓冲区有1个字符，接收串口数据
		m_comm.put_InputLen(0);// SetInputLen(0);  设置当前缓冲区长度为0
		SetDlgItemText(IDC_BTN_OPEN, _T("关闭串口"));
	}
	else
	{
		m_comm.put_PortOpen(FALSE);
		SetDlgItemText(IDC_BTN_OPEN, _T("打开串口"));
	}

}
```

## OnComm事件处理，接收串口数据

```python
void CMSCommDemoDlg::OnCommMscomm1()  //串口接收到数据时触发这一事件
{
  CString strData;
	GetDlgItemText(IDC_EDT_DATA, strData);  //获得当前文本框内的字符内容，接收到数据后，在此内容基础上增加数据
	if (m_comm.get_CommEvent() == 2)  //事件值为2表示接收缓冲区内有字符 
	{
		char str[1024] = { 0 };  //设置一个字符串数组
		long k;
		VARIANT InputData = m_comm.get_Input();	//读缓冲区
		COleSafeArray fs;
		fs = InputData;	//VARIANT型变À量转换为COleSafeArray型变量
		for (k = 0; k < (long)fs.GetOneDimSize(); k++)  //(long)fs.GetOneDimSize()  有效数据长度
			fs.GetElement(&k, str + k);	//转换为char型数组

		strData += str;      //	接收到编辑框里面

		SetDlgItemText(IDC_EDT_DATA, strData);  //编辑框内容更新
	}
}
```

## 串口发送消息

- 最简单的发送数据的示例

```python
void CMSCommDemoDlg::OnBnClickedBtnSendData()
{
   CString str；
   GetDlgItemText(IDC_EDIT_SEND,str); // 发送编辑框的数据
   m_Comm.put_Output(COleVariant(str));//发送数据
}
```
- 也可以通过一个byte数组发送数据，可以与下位机之间设置通信协议相关的处理

```python
  CByteArray hextemp;  //声明动态字节数组
	hextemp.SetSize(14);  //数组大小
	int intdataSend;
	hextemp[0] = 0xAA;
	hextemp[1] = 0x02;
	hextemp[2] = 0x01;
	hextemp[3] = 0x02;
	hextemp[12] = 0x00;
	hextemp[13] = 0x55;   //以上，自定义的数据头和数据尾，与下位机处理相关
	intdataSend = round((theta1) * 10);  //theta1是实现定义的double类型的变量
	hextemp[4] = (intdataSend & 0xff00) >> 8;  //将theta1用两个字节表示，下同
	hextemp[5] = (intdataSend & 0x00ff);
	intdataSend = round((speed1) * 10);
	hextemp[6] = (intdataSend & 0xff00) >> 8;
	hextemp[7] = (intdataSend & 0x00ff);
	intdataSend = round((theta2) * 10);
	hextemp[8] = (intdataSend & 0xff00) >> 8;
	hextemp[9] = (intdataSend & 0x00ff);
	intdataSend = round((speed2) * 10);
	hextemp[10] = (intdataSend & 0xff00) >> 8;
	hextemp[11] = (intdataSend & 0x00ff);
	try
	{
		m_comm.put_Output((COleVariant)hextemp);  //COleVariant 强制类型转换，转换为VARIANT类型
		
	}
	catch (double)  //发送出错
	{
		AfxMessageBox(_T("数据发送错误！"));
		return;
	}
```
  
