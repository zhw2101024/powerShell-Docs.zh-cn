---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法"
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法

将配置文档发送到托管节点，并使用配置代理应用配置。

<a id="syntax" class="xliff"></a>
语法
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
参数
----------

ConfigurationData \[in\]  
配置的环境数据。

force \[in\]  
为 **true**，则强制停止配置。

<a id="return-value" class="xliff"></a>
## 返回值
------------

如果成功，则返回零；否则返回错误代码。

<a id="remarks" class="xliff"></a>
## 备注

这是一种静态方法。

<a id="requirements" class="xliff"></a>
## 要求
------------
>**MOF：** DscCore.mof

>**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## 另请参阅


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



