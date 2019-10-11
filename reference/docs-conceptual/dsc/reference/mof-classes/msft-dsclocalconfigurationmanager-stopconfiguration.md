---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: StopConfiguration 方法
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953354"
---
# <a name="stopconfiguration-method"></a>StopConfiguration 方法

停止正在进行的配置更改。

## <a name="syntax"></a>语法

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>参数

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
