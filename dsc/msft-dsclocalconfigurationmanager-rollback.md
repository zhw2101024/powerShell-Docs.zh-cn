---
title: "MSFT_DSCLocalConfigurationManager 类的 RollBack 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a

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


 

 






<!--HONumber=Jun16_HO4-->


