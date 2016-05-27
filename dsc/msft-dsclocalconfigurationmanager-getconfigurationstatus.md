---
title:  MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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
如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 **true**。

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


 

 





<!--HONumber=May16_HO3-->


