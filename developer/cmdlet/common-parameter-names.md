---
title: 常见的参数名称 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059654"
---
# <a name="common-parameter-names"></a>常见参数名称

本主题中所述的参数*通用参数*。 它们由 Windows PowerShell 运行时添加到 cmdlet，并不能声明为 cmdlet。

> [!NOTE]
> 这些参数也会添加到提供程序 cmdlet 和函数使用修饰`CmdletBinding`属性。

## <a name="general-common-parameters"></a>常规常见参数

以下参数添加到所有 cmdlet 和可访问，无论何时运行该 cmdlet。 这些参数定义由[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)类。

### <a name="debug-alias-db"></a>调试 (别名： db)

数据类型：SwitchParameter

此参数指定是否程序员级别调试消息，可以显示在命令行。 这些消息用于故障排除的 cmdlet，该操作，并通过调用生成[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 调试消息不需要本地化。

### <a name="erroraction-alias-ea"></a>ErrorAction (别名： ea)

数据类型：枚举

此参数指定发生错误时采取的操作应发生。 此参数的可能值定义由[System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)枚举。

### <a name="errorvariable-alias-ev"></a>ErrorVariable (别名： ev)

数据类型：字符串

此参数指定要在其中发生错误时放置对象的变量。 若要将追加到此变量，使用 +*varname*而不是清除并设置变量。

### <a name="outvariable-alias-ov"></a>OutVariable (别名： 时，可以选择)

数据类型：字符串

此参数指定要在其中放置所有输出由 cmdlet 生成的对象的变量。 若要将追加到此变量，使用 +*varname*而不是清除并设置变量。

### <a name="outbuffer-alias-ob"></a>OutBuffer (别名： ob)

数据类型：Int32

此参数定义要在管道向下传递的任何对象之前，在输出缓冲区中存储对象的数。 默认情况下，通过管道向下立即传递的对象中。

### <a name="verbose-alias-vb"></a>详细 (别名： vb)

数据类型：SwitchParameter

此参数指定是否该 cmdlet 将写入可以显示在命令行的解释性消息。 这些消息用于提供给用户，更多帮助，并通过调用生成[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。

### <a name="warningaction-alias-wa"></a>WarningAction (别名： 华盛顿州)

数据类型：枚举

此参数指定该 cmdlet 将写入一条警告消息时采取的操作应该发生。 此参数的可能值定义由[System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)枚举。

### <a name="warningvariable-alias-wv"></a>WarningVariable (别名： 西弗吉尼亚州)

数据类型：字符串

此参数指定要在其中保存警告消息的变量。 若要将追加到此变量，使用 +*varname*而不是清除并设置变量。

## <a name="risk-mitigation-parameters"></a>风险缓解参数

以下参数添加到请求确认，才执行其操作的 cmdlet。 确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。 这些参数定义由[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)类。

### <a name="confirm-alias-cf"></a>确认 (别名： cf)

数据类型：SwitchParameter

此参数指定该 cmdlet 是否显示提示，询问用户是否确定要继续。

### <a name="whatif-alias-wi"></a>WhatIf (别名： wi)

数据类型：SwitchParameter

此参数指定该 cmdlet 是否写入一条消息，说明不实际在执行任何操作的情况下运行该 cmdlet 的效果。

## <a name="transaction-parameters"></a>事务参数

以下参数添加到支持事务的 cmdlet。 这些参数定义由[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)类。

### <a name="usetransaction-alias-usetx"></a>UseTransaction (别名： usetx)

数据类型：SwitchParameter

此参数指定该 cmdlet 是否将使用当前事务执行其操作。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
