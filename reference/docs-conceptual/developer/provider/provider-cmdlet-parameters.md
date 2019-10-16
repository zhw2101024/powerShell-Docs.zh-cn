---
title: 提供程序 cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366306"
---
# <a name="provider-cmdlet-parameters"></a>提供程序 cmdlet 参数

提供程序 cmdlet 附带一组静态参数，这些参数可用于支持 cmdlet 的所有提供程序，以及在用户为提供程序 cmdlet 的某些静态参数指定特定值时添加的动态参数。

## <a name="provider-cmdlet-static-parameters"></a>提供程序 Cmdlet 静态参数

静态参数由 Windows PowerShell 定义。 许多参数由 Windows PowerShell 实现，以在所有提供程序之间提供一致性，并提供更简单的开发体验。 这些参数的示例包括 `literalPath`、`exclude` 和 @no__t cmdlet 的 @no__t 参数。 可以覆盖这些参数的较小集，以提供特定于提供程序的操作。 这些参数的示例包括 @no__t cmdlet 的 @no__t 0 和 @no__t 参数。 下面是可为提供程序 cmdlet 覆盖的参数的列表。

`Clear-Content` cmdlet 可以通过实现[Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，定义提供程序如何使用传递到 `Clear-Content` cmdlet 的 @no__t 参数的值的方式进行操作。

`Clear-Item` cmdlet 可以通过实现[Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，定义提供程序如何使用传递到 `Clear-Item` cmdlet 的 @no__t 参数的值的方式进行操作。

@no__t cmdlet，可以通过实现[Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式进行定义的方法。

@no__t cmdlet，你可以通过实现 CopyItem 来定义提供程序如何使用传递 @no__t 给 @no__t cmdlet 的第1级、`Destination` 和 @no__t 3 参数的值。 [ContainerCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 。付款方式.

ChildItems cmdlet 你可以通过实现 Containercmdletprovider 来定义提供程序如何使用传递给 `Get-ChildItem` cmdlet 的 @no__t 值和 @no__t 参数的值。 [Getchilditems *。 *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)和[Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法的。

`Get-Content` cmdlet 可以通过实现[Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，定义提供程序如何使用传递到 `Get-Content` cmdlet 的 @no__t 参数的值的方式进行操作。

`Get-Item` cmdlet 可以通过实现[Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，定义提供程序如何使用传递到 `Get-Item` cmdlet 的 @no__t 参数的值的方式进行操作。

@no__t cmdlet，可以通过实现[Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式进行定义的方法。

`Invoke-Item` cmdlet 可以通过实现[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定义提供程序如何使用传递到 `Invoke-Item` cmdlet 的 @no__t 参数的值的方式进行操作。

@no__t cmdlet，可以通过实现[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式进行定义的方法。

@no__t cmdlet，你可以通过实现 Newitem 来定义提供程序如何使用传递给 @no__t cmdlet 的 `Path`、`ItemType` 和 @no__t 3 参数的值。 [Containercmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 。付款方式.

`New-ItemProperty` cmdlet 可以通过 Newproperty * 来定义提供程序将如何使用传递 @no__t 给 @no__t cmdlet 的第1级、`Name`、@no__t 和 @no__t 参数的值。 [Registryprovider. *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty)付款方式.

`Remove-Item` 您可以通过实现[Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式来实现。

`Remove-ItemProperty` 您可以通过实现 Removeproperty 来定义您的提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值。 [*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)付款方式.

@no__t cmdlet，可以通过实现[Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式进行定义的方法。

`Rename-ItemProperty` 您可以通过实现 Renameproperty，定义提供程序如何使用传递 @no__t 给 @no__t cmdlet 的第1级、`NewName` 和 @no__t 3 参数的值。 [Idynamicpropertycmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)方法。

`Set-Content` cmdlet 可以通过实现[Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法，定义提供程序如何使用传递到 `Set-Content` cmdlet 的 @no__t 参数的值的方式进行操作。

@no__t cmdlet，可以通过实现[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，定义提供程序如何使用传递给 @no__t cmdlet 的第 1 @no__t 和 @no__t 参数的值的方式进行定义的方法。

@no__t cmdlet，可以通过实现[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，定义提供程序如何使用传递给 @no__t cmdlet 的 `Path` 和 @no__t 参数的值的方式来实现此操作。

`Test-Path` cmdlet 可以通过实现[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定义提供程序如何使用传递到 `Test-Path` cmdlet 的 @no__t 参数的值的方式进行操作。

此外，不能指定这些参数的特征，例如它们是否是可选的或必需的，也不能为这些参数指定别名或指定任何验证属性。 与此相反，你可以通过使用 `Parameters` 属性之类的属性在独立 cmdlet 中指定参数特征。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 Cmdlet 动态参数

Cmdlet 提供程序的动态参数类似于独立 cmdlet 的动态提供程序。 在这两种情况下，当用户为一个默认参数（如 @no__t 的参数）指定特定值时，将参数添加到 cmdlet。 但是，并非所有静态参数都可用于触发动态参数的添加。 有关动态参数的详细信息，请参阅[提供程序 Cmdlet 动态参数](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另请参阅

[提供程序 Cmdlet 动态参数](./provider-cmdlet-dynamic-parameters.md)

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)