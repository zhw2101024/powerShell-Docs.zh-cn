---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '获取用于控制配置代理的本地配置管理器设置。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getmetaconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法

获取用于控制配置代理的本地配置管理器设置。

语法
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

参数
----------

*MetaConfiguration* \[out\]  
在返回时包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。

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


