---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 类的 GetConfigurationStatus 方法

获取配置状态历史记录。

<a id="syntax" class="xliff"></a>
语法
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a id="parameters" class="xliff"></a>
参数
----------

All \[in\]  
如果此方法应返回计算机上运行的所有配置的相关信息（包括配置应用程序和一致性检查），则为 **true**。

configurationStatus \[out\]  
返回时，包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。

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


 

 



