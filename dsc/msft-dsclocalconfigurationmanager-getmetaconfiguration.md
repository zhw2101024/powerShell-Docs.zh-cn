---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892835"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 GetMetaConfiguration 方法

获取用于控制配置代理的本地配置管理器设置。

## <a name="syntax"></a>语法

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>参数

MetaConfiguration \[out\]：返回响应时，包含定义设置的 MSFT_DSCMetaConfiguration 类的嵌入实例。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)