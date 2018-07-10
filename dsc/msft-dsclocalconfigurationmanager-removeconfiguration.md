---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892678"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法

删除配置文件。

## <a name="syntax"></a>语法

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>参数

Stage \[in\]：指定要删除的配置文档。 下面的值是有效的：

|值 |说明 |
|:--- |:---|
|**1** | **当前**配置文档 (current.mof)。 |
|**2** | **挂起的**配置文档 (pending.mof)。  |
|**4** | **以前的**配置文档 (previous.mof)。 |

Force \[in\]：若为 true，强制删除配置。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)