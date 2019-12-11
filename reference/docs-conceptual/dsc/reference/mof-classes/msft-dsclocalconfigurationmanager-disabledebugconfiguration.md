---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DisableDebugConfiguration 方法
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955054"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration 方法

禁用 DSC 资源调试。

## <a name="syntax"></a>语法

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>参数

此方法没有任何参数。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
