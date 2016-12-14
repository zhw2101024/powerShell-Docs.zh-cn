---
title: "MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4f3d74949d98e3ab3f5136303e229c23ed903c5d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法

删除配置文件。

<a name="syntax"></a>语法
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>参数
----------

Stage \[in\]  
指定要删除的配置文档。 下面的值是有效的：

|值 |说明 |
|:--- |:---|
|**1** | **当前**配置文档 (current.mof)。 |
|**2** | **挂起的**配置文档 (pending.mof)。  |
|**4** | **以前的**配置文档 (previous.mof)。 |

Force \[in\]  
为 **true**，则强制删除配置。

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


 

 



