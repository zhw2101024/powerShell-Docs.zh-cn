---
title: "MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0777467d37e2f5588f9c0ef368148e3bea963a5b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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


 

 



