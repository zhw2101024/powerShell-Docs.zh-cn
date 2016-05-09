---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '获取配置状态历史记录。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法

获取配置状态历史记录。

语法
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

参数
----------

*All* \[in\]  
如果此方法返回在计算机上运行的所有配置的相关信息，则为 **true**（这些信息包括
配置应用程序和一致性检查）。

*configurationStatus* \[out\]  
返回时，包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。

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


