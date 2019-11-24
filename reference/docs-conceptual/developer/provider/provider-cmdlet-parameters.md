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

静态参数由 Windows PowerShell 定义。 许多参数由 Windows PowerShell 实现，以在所有提供程序之间提供一致性，并提供更简单的开发体验。 这些参数的示例包括 `Get-Item` cmdlet 的 `literalPath`、`exclude`和 `include` 参数。 可以覆盖这些参数的较小集，以提供特定于提供程序的操作。 这些参数的示例包括 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数。 下面是可为提供程序 cmdlet 覆盖的参数的列表。

`Clear-Content` cmdlet，你可以通过实现[Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，定义提供程序如何使用传递给 `Clear-Content` cmdlet 的 `Path` 参数的值。

`Clear-Item` cmdlet，你可以通过实现[Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，定义提供程序如何使用传递给 `Clear-Item` cmdlet 的 `Path` 参数的值。

`Clear-ItemProperty` cmdlet，可以通过实现[Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，定义提供程序将如何使用传递给 `Clear-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数的值。

`Copy-Item` cmdlet，可以通过实现[CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，定义提供程序将如何使用传递给 `Copy-Item` cmdlet 的 `Path`、`Destination`和 `Recurse` 参数的值的方式。

ChildItems cmdlet 可以通过实现[Containercmdletprovider 和 Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，定义提供程序如何使用传递到 `Get-ChildItem` cmdlet 的 `Path` 和 `Recurse` 参数的值的方式。 * 和。 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法。

`Get-Content` cmdlet，你可以通过实现[Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，定义提供程序如何使用传递给 `Get-Content` cmdlet 的 `Path` 参数的值。

`Get-Item` cmdlet，你可以通过实现[Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，定义提供程序如何使用传递给 `Get-Item` cmdlet 的 `Path` 参数的值。

`Get-ItemProperty` cmdlet，可以通过实现[Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，定义提供程序将如何使用传递给 `Get-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数的值。

`Invoke-Item` cmdlet，你可以通过实现[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定义提供程序如何使用传递给 `Invoke-Item` cmdlet 的 `Path` 参数的值。

`Move-Item` cmdlet，可以通过实现[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法，定义提供程序将如何使用传递给 `Move-Item` cmdlet 的 `Path` 和 `Destination` 参数的值。

`New-Item` cmdlet，可以通过实现[Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，定义提供程序将如何使用传递给 `New-Item` cmdlet 的 `Path`、`ItemType`和 `Value` 参数的值的方式。

`New-ItemProperty` cmdlet，可以通过实现[Newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty)方法，定义提供程序如何使用传递给 `Value` cmdlet 的 `Path`、`Name`、`PropertyType`和 `New-ItemProperty` 参数的值。

`Remove-Item` 可以通过实现[Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，定义提供程序将如何使用传递给 `Remove-Item` cmdlet 的 `Path` 和 `Recurse` 参数的值的方式。

`Remove-ItemProperty` 可以通过实现[Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)方法，定义提供程序将如何使用传递给 `Remove-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数的值的方式。

`Rename-Item` cmdlet，可以通过实现[Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，定义提供程序将如何使用传递给 `Rename-Item` cmdlet 的 `Path` 和 `NewName` 参数的值。

`Rename-ItemProperty` 可以通过实现[Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)方法，定义提供程序将如何使用传递给 `Rename-ItemProperty` cmdlet 的 `Path`、`NewName`和 `Name` 参数的值的方式。

`Set-Content` cmdlet，你可以通过实现[Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法，定义提供程序如何使用传递给 `Set-Content` cmdlet 的 `Path` 参数的值。

`Set-Item` cmdlet，可以通过实现[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，定义提供程序将如何使用传递给 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数的值。

`Set-ItemProperty` cmdlet，可以通过实现[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，定义提供程序将如何使用传递给 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数的值。

`Test-Path` cmdlet，你可以通过实现[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定义提供程序如何使用传递给 `Test-Path` cmdlet 的 `Path` 参数的值。

此外，不能指定这些参数的特征，例如它们是否是可选的或必需的，也不能为这些参数指定别名或指定任何验证属性。 与此相反，你可以使用属性（如 `Parameters` 属性）在独立的 cmdlet 中指定参数特征。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 Cmdlet 动态参数

Cmdlet 提供程序的动态参数类似于独立 cmdlet 的动态提供程序。 在这两种情况下，当用户为某个默认参数（如 `path` 参数）指定特定值时，将参数添加到 cmdlet。 但是，并非所有静态参数都可用于触发动态参数的添加。 有关动态参数的详细信息，请参阅[提供程序 Cmdlet 动态参数](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另请参阅

[提供程序 Cmdlet 动态参数](./provider-cmdlet-dynamic-parameters.md)

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)