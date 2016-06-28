---
title: "MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 8f13964dfbbe1cd827c58232a35d1cbacddeed1b

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

 

 






<!--HONumber=Jun16_HO4-->


