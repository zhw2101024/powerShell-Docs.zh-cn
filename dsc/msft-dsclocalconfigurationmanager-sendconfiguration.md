---
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 95b141472d9428cee71b6970fc1f496704211c0b

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


 

 






<!--HONumber=Jun16_HO4-->


