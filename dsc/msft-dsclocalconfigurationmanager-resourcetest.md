---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法"
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法

直接调用 DSC 资源的 **Test** 方法。

<a name="syntax"></a>语法
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
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

InDesiredState \[out\]  
返回时，如果目标节点处于所需状态，会将此属性设置为 **true**。

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


 

 



