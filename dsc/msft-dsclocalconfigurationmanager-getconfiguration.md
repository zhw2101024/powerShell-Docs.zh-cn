---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '将配置文档发送到托管节点，并使用配置代理，通过 Get 方法应用配置。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 GetConfiguration 方法

将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。

语法
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

参数
----------

*configurationData* \[in\]  
指定要发送的配置数据。

*configurations* \[out\]  
在返回时包含配置的嵌入实例。

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


