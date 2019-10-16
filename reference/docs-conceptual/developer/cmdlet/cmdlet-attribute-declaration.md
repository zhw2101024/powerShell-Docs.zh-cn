---
title: Cmdlet 特性声明 |Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363536"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 属性声明

Cmdlet 属性将 Microsoft .NET 框架类标识为 Cmdlet，并指定用于调用 cmdlet 的动词和名词。

## <a name="syntax"></a>语法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>参数

需要 `VerbName` （[system.string](/dotnet/api/System.String)）。 指定 cmdlet 谓词。 此谓词指定 cmdlet 执行的操作。 有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)和[所需的开发指南](./required-development-guidelines.md)。

需要 `NounName` （[system.string](/dotnet/api/System.String)）。 指定 cmdlet 名词。 此名词指定该 cmdlet 作用于的资源。 有关 cmdlet 名词的详细信息，请参阅[Cmdlet 声明](./cmdlet-class-declaration.md)和[强烈建议开发指南](./strongly-encouraged-development-guidelines.md)。

@no__t-[0 （system.string](/dotnet/api/System.Boolean)）可选命名参数。 `True` 指示 cmdlet 支持对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用，该方法为 cmdlet 提供了一种在执行更改系统的操作之前提示用户的方法。 @no__t 为0（默认值），则指示该 cmdlet 不支持对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用。 有关确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

@no__t 为0（[Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)）可选的命名参数。 指定应通过对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用来确认 cmdlet 的操作的时间的。 仅当 Cmdlet 的 ConfirmImpact 值（默认情况下，Medium）等于或大于 `$ConfirmPreference` 变量的值时，才会调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 。 仅当指定了 @no__t 0 参数时，才应指定此参数。

`DefaultParameterSetName` （[system.string](/dotnet/api/System.String)）可选命名参数。 指定 Windows PowerShell 运行时在无法确定要使用哪个参数时尝试使用的默认参数集。 请注意，可以通过使每个参数的唯一参数设置一个必需的参数来消除这种情况。

在这种情况下，即使指定了默认参数集名称，Windows PowerShell 也无法使用默认参数集。 Windows PowerShell 运行时无法仅基于对象类型区分参数集。 例如，如果你有一个参数集，该参数集采用字符串作为文件路径，而另一个组直接采用**FileInfo**对象，则 Windows PowerShell 无法根据传递给 cmdlet 的值来确定要使用的参数集，也不会使用默认参数集。 在这种情况下，即使指定默认参数集名称，Windows PowerShell 也会引发不明确的参数集错误消息。

@no__t-[0 （system.string](/dotnet/api/System.Boolean)）可选命名参数。 `True` 指示该 cmdlet 可以在事务中使用。 当指定 `True` 时，Windows PowerShell 运行时将 @no__t 参数添加到 cmdlet 的参数列表中。 @no__t 为0（默认值），则指示不能在事务中使用 cmdlet。

## <a name="remarks"></a>备注

- 同时，动词和名词用于标识已注册的 cmdlet，并在脚本中调用 cmdlet。

- 当从 Windows PowerShell 控制台调用 cmdlet 时，该命令将类似于以下命令：

**VerbName-NounName**

- 声明 Cmdlet 属性时，在 Windows PowerShell 外部更改资源的所有 cmdlet 都应包含 `SupportsShouldProcess` 关键字，这允许 Cmdlet 在[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前调用cmdlet 执行其操作。 如果[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用返回 `false`，则不应执行该操作。 有关[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用生成的确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

@No__t-0 和 @no__t cmdlet 参数仅可用于支持[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用的 cmdlet 的 cmdlet。

## <a name="example"></a>示例

下面的类定义使用 Cmdlet 特性来标识用于检索有关在本地计算机上运行的进程的信息的**get-help** Cmdlet 的 .NET Framework 类。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

有关 GetProc **cmdlet 的**详细信息，请参阅[教程](./getproc-tutorial.md)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
