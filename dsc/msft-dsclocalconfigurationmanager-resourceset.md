---
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: cbc499f293aad941d40fcb720ef53e832c3b1ea8

---


# MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法

直接调用 DSC 资源的 **Set** 方法。

语法
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

参数
----------

*ResourceType* \[in\]  
要调用的资源的名称。

*ModuleName* \[in\]  
包含要调用的资源的模块名称。

*resourceProperty* \[in\]  
分别在哈希表中将资源属性名称及其值指定为键和值。 使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。

*RebootRequired* \[out\]  
返回时，如果目标节点需要重启，会将此属性设置为 **true**。

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


