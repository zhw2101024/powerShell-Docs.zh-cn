---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '将配置文档发送到托管节点并将其保存为挂起。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法

将配置文档发送到托管节点并将其保存为挂起的更改。

语法
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

参数
----------

*ConfigurationData* \[in\]  
配置的环境数据。

*force* \[in\]  
为 **true**，则强制停止配置。

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


