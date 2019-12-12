---
title: 常见参数名称 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365736"
---
# <a name="common-parameter-names"></a>常见参数名称

本主题中描述的参数称为*通用参数*。 它们由 Windows PowerShell 运行时添加到 cmdlet 中，不能由 cmdlet 声明。

> [!NOTE]
> 还会将这些参数添加到提供程序 cmdlet 以及用 `CmdletBinding` 特性修饰的函数。

## <a name="general-common-parameters"></a>一般常见参数

以下参数将添加到所有 cmdlet 中，并可在每次运行 cmdlet 时访问。 这些参数是由[Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)类定义的。

### <a name="debug-alias-db"></a>调试（别名： db）

数据类型： SwitchParameter

此参数指定是否可以在命令行中显示的程序员级调试消息。 这些消息用于对 cmdlet 的操作进行故障排除，并由对[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的调用生成。 调试消息无需本地化。

### <a name="erroraction-alias-ea"></a>ErrorAction （alias： ea）

数据类型：枚举

此参数指定发生错误时应执行的操作。 此参数的可能值是由[Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)枚举定义的。

### <a name="errorvariable-alias-ev"></a>ErrorVariable （alias： ev）

数据类型：字符串

此参数指定发生错误时要在其中放置对象的变量。 若要追加到此变量，请使用 +*varname* ，而不是清除和设置变量。

### <a name="outvariable-alias-ov"></a>OutVariable （alias： ov-es）

数据类型：字符串

此参数指定在其中放置由 cmdlet 生成的所有输出对象的变量。 若要追加到此变量，请使用 +*varname* ，而不是清除和设置变量。

### <a name="outbuffer-alias-ob"></a>OutBuffer （alias： ob）

数据类型： Int32

此参数定义在将任何对象向下传递管道之前要存储在输出缓冲区中的对象数。 默认情况下，对象会立即沿管道向下传递。

### <a name="verbose-alias-vb"></a>Verbose （alias： vb）

数据类型： SwitchParameter

此参数指定该 cmdlet 是否写入可以在命令行中显示的解释性消息。 这些消息旨在向用户提供其他帮助，并通过对[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的调用来生成它们。

### <a name="warningaction-alias-wa"></a>WarningAction （alias： wa）

数据类型：枚举

此参数指定在 cmdlet 写入警告消息时应执行的操作。 此参数的可能值是由[Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)枚举定义的。

### <a name="warningvariable-alias-wv"></a>WarningVariable （alias： wv）

数据类型：字符串

此参数指定可在其中保存警告消息的变量。 若要追加到此变量，请使用 +*varname* ，而不是清除和设置变量。

## <a name="risk-mitigation-parameters"></a>风险缓解参数

将以下参数添加到 cmdlet，这些 cmdlet 在执行操作之前请求确认。 有关确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。 这些参数是由[Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)类定义的。

### <a name="confirm-alias-cf"></a>确认（别名： cf）

数据类型： SwitchParameter

此参数指定该 cmdlet 是否显示提示，询问用户是否确实要继续。

### <a name="whatif-alias-wi"></a>WhatIf （别名： wi）

数据类型： SwitchParameter

此参数指定该 cmdlet 是否写入一条消息，该消息描述运行 cmdlet 的效果，而不实际执行任何操作。

## <a name="transaction-parameters"></a>事务参数

将以下参数添加到支持事务的 cmdlet。 这些参数是由[Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)类定义的。

### <a name="usetransaction-alias-usetx"></a>UseTransaction （alias： usetx）

数据类型： SwitchParameter

此参数指定该 cmdlet 是否将使用当前事务来执行其操作。

## <a name="see-also"></a>另请参阅

[System.web. Commonparameters。](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.web. Shouldprocessparameters。](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.web. Transactionparameters。](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
