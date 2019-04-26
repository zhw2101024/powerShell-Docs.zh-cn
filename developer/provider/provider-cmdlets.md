---
title: 提供程序 cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080945"
---
# <a name="provider-cmdlets"></a>提供程序 cmdlet

用户可以运行以管理数据存储区的 cmdlet 称为提供程序 cmdlet。 若要支持这些 cmdlet，需要覆盖某些由基本提供程序类和接口定义的方法。

## <a name="provider-cmdlets"></a>提供程序 Cmdlet

下面是可以由用户运行的提供程序 cmdlet:

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet

- `Get-PSDrive`：此 cmdlet 将返回当前会话中的 Windows PowerShell 驱动器。 不需要覆盖任何方法，以支持此 cmdlet。

- `New-PSDrive`：此 cmdlet 允许用户创建 Windows PowerShell 驱动器来访问数据存储区。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

- `Remove-PSDrive`：此 cmdlet 允许用户访问数据存储区的 Windows PowerShell 驱动器中删除。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。

### <a name="item-cmdlets"></a>Item cmdlet

- `Clear-Item`：此 cmdlet 允许用户在数据存储区中删除项的值。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

- `Copy-Item`：此 cmdlet 允许用户将项从一个位置复制到另一个。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

- `Get-Item`：此 cmdlet 允许用户从数据存储中检索数据。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

- `Get-ChildItem`：此 cmdlet 允许用户检索父项的子项。 若要支持此 cmdlet，覆盖以下方法：

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`：此 cmdlet 允许用户执行指定的项的默认操作。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

- `Move-Item`：此 cmdlet 允许用户将项从一个位置移动到另一个位置。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的方法。

- `New-ItemProperty`：此 cmdlet 允许用户在数据存储区中创建新项。

- `Remove-Item`：此 cmdlet 允许用户从数据存储区中删除项目。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

- `Rename-Item`：此 cmdlet 允许用户重命名数据存储中的项目。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

- `Set-Item`：此 cmdlet 允许用户更新的数据存储区中的项的值。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

### <a name="item-content-cmdlets"></a>项内容 cmdlet

- `Add-Content`：此 cmdlet 允许用户将内容添加到项目。

- `Clear-Content`：此 cmdlet 允许用户从注册表项删除内容，而不删除该项。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

- `Get-Content`：此 cmdlet 允许用户检索其内容的项。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法将返回[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)定义接口用于读取内容的方法。

- `Set-Content`：此 cmdlet 允许用户更新项的内容。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法将返回[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)定义接口用于写入内容的方法。

### <a name="item-property-cmdlets"></a>Item 属性 cmdlet

- `Clear-ItemProperty`：此 cmdlet 允许用户删除属性的值。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。

- `Copy-ItemProperty`：此 cmdlet 允许用户将属性和其值从一个位置复制到另一个。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法。

- `Get-ItemProperty`：此 cmdlet 检索项的属性。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

- `Move-ItemProperty`：此 cmdlet 允许用户将属性和其值从一个位置移到另一个。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法。

- `New-ItemProperty`：此 cmdlet 允许用户创建新的属性并将其值设置。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

- `Remove-ItemProperty`：此 cmdlet 允许用户删除一个属性及其值。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

- `Rename-ItemProperty`：此 cmdlet 允许用户更改的属性名称。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

- `Set-ItemProperty`：此 cmdlet 允许用户更新项的属性。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

### <a name="location-cmdlets"></a>位置 cmdlet

- `Get-Location`：检索有关当前工作位置的信息。 不需要覆盖任何方法，以支持此 cmdlet。

- `Pop-Location`：此 cmdlet 将当前位置更改到最近推入堆栈的位置。 不需要覆盖任何方法，以支持此 cmdlet。

- `Push-Location`：此 cmdlet 将当前位置添加到的位置 （"堆栈"） 的列表顶部。 不需要覆盖任何方法，以支持此 cmdlet。

- `Set-Location`：此 cmdlet 将当前的工作位置设置为指定的位置。 不需要覆盖任何方法，以支持此 cmdlet。

### <a name="path-cmdlets"></a>路径 cmdlet

- `Join-Path`：此 cmdlet 允许用户以合并一个父级和子级路径片段来创建提供程序内部的路径。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

- `Convert-Path`：此 cmdlet 将路径从 Windows PowerShell 路径转换为 Windows PowerShell 提供程序路径。

- `Split-Path`：返回指定的路径部分。

- `Resolve-Path`：解析路径中的通配符并显示路径内容。

- `Test-Path`：此 cmdlet 确定路径的所有元素是否都存在。 若要支持此 cmdlet，覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet

- `Get-PSProvider`：此 cmdlet 将返回有关在会话中可用的提供程序的信息。 不需要覆盖任何方法，以支持此 cmdlet。