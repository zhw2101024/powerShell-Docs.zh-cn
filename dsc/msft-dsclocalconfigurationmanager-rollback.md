---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '回滚到以前的配置。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 RollBack 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 RollBack 方法

将配置回滚到以前的版本。

语法
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

参数
----------

*configurationNumber* \[in\]  
指定请求的配置。 

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


