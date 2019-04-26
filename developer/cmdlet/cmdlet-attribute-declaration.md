---
title: Cmdlet 属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068617"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 属性声明

Cmdlet 属性标识为 cmdlet 的 Microsoft.NET Framework 类和指定的谓词和名词用于调用该 cmdlet。

## <a name="syntax"></a>语法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>参数

`VerbName` ([System.String](/dotnet/api/System.String)) 所需。 指定 cmdlet 动词。 此谓词指定该 cmdlet 所执行的操作。 有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)并[所需开发指导原则](./required-development-guidelines.md)。

`NounName` ([System.String](/dotnet/api/System.String)) 所需。 指定 cmdlet 名词。 此名词指定 cmdlet 作用于的资源。 有关 cmdlet 名词的详细信息，请参阅[Cmdlet 声明](./cmdlet-class-declaration.md)并[强烈推荐的开发指南](./strongly-encouraged-development-guidelines.md)。

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示该 cmdlet 支持调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，为该 cmdlet 提供了一种方法来执行更改系统的操作前提示用户。 `False`默认值，指示该 cmdlet 不支持调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 可选的命名参数。 指定该 cmdlet 的操作时应通过调用确认[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （默认为 Medium） cmdlet 的 ConfirmImpact 值等于或大于的值时只会调用`$ConfirmPreference`变量。 应指定此参数仅当`SupportsShouldProcess`指定参数。

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) 可选的命名参数。 指定 Windows PowerShell 运行时尝试使用时不能确定哪个参数设置为使用默认参数集。 请注意，可以设置必需参数的唯一参数的每个参数，从而消除这种情况。

没有一种情况下，Windows PowerShell 不能使用的默认参数集，即使指定默认参数集名称。 Windows PowerShell 运行时无法区分仅根据对象类型的参数集。 例如，如果有一个参数集的文件路径，以及另一组采用一个字符串，采用**FileInfo**对象直接，Windows PowerShell 不能确定哪个参数设置为使用基于传递给的值cmdlet，也不会使用默认参数集。 在这种情况下，即使指定默认参数集名称，Windows PowerShell 将引发不明确的参数集错误消息。

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示可以在一个事务内使用此 cmdlet。 当`True`未指定，则 Windows PowerShell 运行时添加`UseTransaction`到该 cmdlet 的参数列表的参数。 `False`默认值，指示不能在事务中使用此 cmdlet。

## <a name="remarks"></a>备注

- 在一起，动词和名词可用来识别你已注册的 cmdlet 并调用你在脚本中的 cmdlet。

- 从 Windows PowerShell 控制台中调用 cmdlet 时，该命令类似于以下命令：

**VerbName-NounName**

- 更改资源在 Windows PowerShell 之外的所有 cmdlet 应都包括`SupportsShouldProcess`关键字声明 Cmdlet 属性，它允许该 cmdlet 将调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前该 cmdlet 将执行其操作。 如果[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用返回`false`，不应执行操作。 有关生成的确认请求的详细信息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

`Confirm`并`WhatIf`cmdlet 参数是仅适用于支持的 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用。

## <a name="example"></a>示例

以下类定义使用 Cmdlet 属性标识的.NET Framework 类**Get-proc** cmdlet 检索有关本地计算机上运行的进程的信息。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

有关详细信息**Get-proc** cmdlet，请参阅[GetProc 教程](./getproc-tutorial.md)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
