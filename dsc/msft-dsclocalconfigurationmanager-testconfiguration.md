---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法

将配置文档发送到托管节点并针对该文档验证当前配置。

<a name="syntax"></a>语法
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>参数
----------

configurationData \[in\]  
配置的环境数据。

InDesiredState \[out\]  
返回时，指定托管节点是否处于配置文档指定的状态。

ResourcesInDesiredState \[out\]  
返回时，包含 **MSFT_ResourceInDesiredState** 类的嵌入实例，该类指定处于所需状态的资源。

ResourcesNotInDesiredState \[out\]  
返回时，包含 **MSFT_ResourceNotInDesiredState** 类的嵌入实例，该类指定未在所需状态的资源。

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


 

 



