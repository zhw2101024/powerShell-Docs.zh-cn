---
title: "MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4662bfed62fce47be7d42a083ad5a7be801e6ff1
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法

获取用于控制配置代理的本地配置管理器设置。

<a name="syntax"></a>语法
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>参数
----------

MetaConfiguration \[out\]  
在返回时包含定义设置的 **MSFT_DSCMetaConfiguration** 类的嵌入实例。

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


 

 



