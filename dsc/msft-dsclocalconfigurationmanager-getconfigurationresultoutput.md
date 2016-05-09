---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '检索与特定作业相关的配置代理输出。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationresultoutput'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法

获取与特定作业相关的配置代理输出。

语法
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

参数
----------

*jobId* \[in\]  
要为其获取输出数据的作业 ID。

*resumeOutputBookmark* \[in\]  
指定输出应从上一个书签中延续。

*output* \[out\]  
指定作业的输出。

## 返回值
------------

如果成功，则返回零；否则返回错误代码。

## 备注

这是一种静态方法。

## 要求
------------
>**MOF：** DscCore.mof

>**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration


## 另请参阅


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 





<!--HONumber=Apr16_HO2-->


