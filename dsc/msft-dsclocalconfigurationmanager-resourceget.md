---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法"
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法

直接调用 DSC 资源的 **Get** 方法。

<a name="syntax"></a>语法
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>参数
----------

ResourceType \[in\]  
要调用的资源的名称。

ModuleName \[in\]  
包含要调用的资源的模块名称。

resourceProperty \[in\]  
分别在哈希表中将资源属性名称及其值指定为键和值。 使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。

configurations \[out\]  
在返回时包含配置的嵌入实例。

## <a name="return-value"></a>返回值
------------

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求
------------
>**MOF：** DscCore.mof

>**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>另请参阅


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



