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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057036"
---
# <a name="provider-cmdlet-parameters"></a>提供程序 cmdlet 参数

提供程序 cmdlet 都具有一组可用于支持该 cmdlet 的所有提供程序的静态参数，以及为动态参数在用户指定的提供程序 cmdlet 某些静态参数的某些值时添加。

## <a name="provider-cmdlet-static-parameters"></a>提供程序 Cmdlet 静态参数

由 Windows PowerShell 定义的静态参数。 这些参数的一大组是所有提供程序提供一致性并提供更简单的开发体验的 Windows powershell 实现的。 这些参数的示例包括`literalPath`， `exclude`，并`include`的参数`Get-Item`cmdlet。 若要提供特定于您的提供程序的操作时可以覆盖较小的这些参数集。 这些参数的示例包括`Path`并`Value`参数的`Set-Item`cmdlet。 下面是可以被覆盖的提供程序 cmdlet 的参数的列表。

`Clear-Content` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Clear-Content`cmdlet 通过实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法。

`Clear-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Clear-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法。

`Clear-ItemProperty` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`Name`的参数`Clear-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法。

`Copy-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`， `Destination`，并`Recurse`的参数`Copy-Item`cmdlet 通过实现[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法。

可以定义您的提供程序使用传递给的值的方式获取 ChildItems cmdlet`Path`并`Recurse`的参数`Get-ChildItem`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)并[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法。

`Get-Content` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Get-Content`cmdlet 通过实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法。

`Get-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Get-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法。

`Get-ItemProperty` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`Name`的参数`Get-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法。

`Invoke-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Invoke-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

`Move-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`Destination`的参数`Move-Item`cmdlet 通过实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。

`New-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`， `ItemType`，并`Value`的参数`New-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法。

`New-ItemProperty` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`， `Name`， `PropertyType`，和`Value`的参数`New-ItemProperty`cmdlet 通过实现[Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty)方法。

`Remove-Item` 可以定义您的提供程序使用传递给的值的方式`Path`并`Recurse`的参数`Remove-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法。

`Remove-ItemProperty` 可以定义您的提供程序使用传递给的值的方式`Path`并`Name`的参数`Remove-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)方法。

`Rename-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`NewName`的参数`Rename-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。

`Rename-ItemProperty` 可以定义您的提供程序使用传递给的值的方式`Path`， `NewName`，并`Name`的参数`Rename-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)方法。

`Set-Content` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Set-Content`cmdlet 通过实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法。

`Set-Item` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`Value`的参数`Set-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法。

`Set-ItemProperty` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`并`Value`的参数`Set-Item`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法。

`Test-Path` cmdlet 可以定义您的提供程序使用传递给的值的方式`Path`的参数`Test-Path`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

此外，不能指定这些参数，它们是可选或必需的如的特征也您可以为这些参数提供一个别名或指定任何验证特性。 与此相反，您可以指定参数特征在独立的 cmdlet 中使用属性类似于`Parameters`属性。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 Cmdlet 的动态参数

为 cmdlet 提供程序的动态参数是类似于独立 cmdlet 的动态提供程序。 在这两种情况下，参数添加到该 cmdlet 时用户指定特定值的其中一个默认参数，例如`path`参数。 但是，并非所有的静态参数可用于触发动态参数添加。 有关动态参数的详细信息，请参阅[提供程序 Cmdlet 的动态参数](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另请参阅

[提供程序 Cmdlet 的动态参数](./provider-cmdlet-dynamic-parameters.md)

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)