---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法

使用任务计划程序启动一致性检查。

<a id="syntax" class="xliff"></a>
语法
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a id="parameters" class="xliff"></a>
参数
----------

Flags \[in\]  
指定要运行的一致性检查类型的位掩码。 以下值有效，并可以通过 **OR** 位运算组合：

|值 |说明 |
|:--- |:---|
|**1** | 常规的一致性检查。 |
|**2** | 重启后一致性检查的延续。 此值不应与其他值组合。 |
|**4** | 应从节点的元配置中指定的请求服务器请求配置。 此值应始终与 **1** 组合，以获得为 **5** 的值。 |
|**8** | 将状态发送到报表服务器。 |

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


 

 



