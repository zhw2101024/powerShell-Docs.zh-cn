---
title: "MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 9721486cca6f94d6b156c6ee1992eced6652c123

---

# MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法

停止正在进行的配置更改。

语法
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

参数
----------

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


