---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: SendMetaConfigurationApply 方法
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727041"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply 方法

设置用于控制配置代理的本地配置管理器设置。

## <a name="syntax"></a>语法

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>参数

ConfigurationData  \[in\]：配置的环境数据。

force  \[in\]：若为 true  ，强制停止配置。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
