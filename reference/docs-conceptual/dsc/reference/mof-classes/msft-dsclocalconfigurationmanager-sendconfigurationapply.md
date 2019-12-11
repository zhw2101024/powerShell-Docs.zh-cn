---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: SendConfigurationApply 方法
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954884"
---
# <a name="sendconfigurationapply-method"></a>SendConfigurationApply 方法

将配置文档发送到托管节点，并使用配置代理应用配置。

## <a name="syntax"></a>语法

```mof
uint32 SendConfigurationApply(
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
