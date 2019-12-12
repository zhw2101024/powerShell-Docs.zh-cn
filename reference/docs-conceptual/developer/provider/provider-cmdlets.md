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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359976"
---
# <a name="provider-cmdlets"></a>提供程序 cmdlet

用户可以运行以管理数据存储的 cmdlet 称为提供程序 cmdlet。 若要支持这些 cmdlet，你需要覆盖由基提供程序类和接口定义的某些方法。

## <a name="provider-cmdlets"></a>提供程序 Cmdlet

下面是可以由用户运行的提供程序 cmdlet：

### <a name="psdrive-cmdlets"></a>New-psdrive cmdlet

- `Get-PSDrive`：此 cmdlet 将返回当前会话中的 Windows PowerShell 驱动器。 无需覆盖任何方法即可支持此 cmdlet。

- `New-PSDrive`：此 cmdlet 允许用户创建用于访问数据存储区的 Windows PowerShell 驱动器。 若要支持此 cmdlet，请覆盖[Drivecmdletprovider. Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和 Drivecmdletprovider. Newdrivedynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

- `Remove-PSDrive`：此 cmdlet 允许用户删除访问数据存储的 Windows PowerShell 驱动器。 若要支持此 cmdlet，请覆盖[Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。

### <a name="item-cmdlets"></a>项 cmdlet

- `Clear-Item`：此 cmdlet 允许用户删除数据存储中某个项的值。 若要支持此 cmdlet，请覆盖[Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和 Itemcmdletprovider. Clearitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

- `Copy-Item`：此 cmdlet 允许用户将项从一个位置复制到另一个位置。 若要支持此 cmdlet，请覆盖[Containercmdletprovider. Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和 Containercmdletprovider. Copyitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

- `Get-Item`：此 cmdlet 允许用户从数据存储中检索数据。 若要支持此 cmdlet，请覆盖[Itemcmdletprovider. Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和 Itemcmdletprovider. Getitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

- `Get-ChildItem`：此 cmdlet 允许用户检索父项的子项。 若要支持此 cmdlet，请覆盖以下方法：

  - [Getchilditems * 的 Containercmdletprovider *。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [Getchilditemsdynamicparameters * 的 Containercmdletprovider *。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [Getchildnames * 的 Containercmdletprovider *。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [Getchildnamesdynamicparameters * 的 Containercmdletprovider *。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`：此 cmdlet 允许用户执行项指定的默认操作。 若要支持此 cmdlet，请覆盖[Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和 Itemcmdletprovider. Invokedefaultaction 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

- `Move-Item`：此 cmdlet 允许用户将项从一个位置移到另一个位置。 若要支持此 cmdlet，请重写[Navigationcmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s 方法（& s）。

- `New-ItemProperty`：此 cmdlet 允许用户在数据存储中创建新项。

- `Remove-Item`：此 cmdlet 允许用户从数据存储中删除项。 若要支持此 cmdlet，请覆盖[Containercmdletprovider. Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和 Containercmdletprovider. Removeitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

- `Rename-Item`：此 cmdlet 允许用户重命名数据存储区中的项。 若要支持此 cmdlet，请覆盖[Containercmdletprovider. Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和 Containercmdletprovider. Renameitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

- `Set-Item`：此 cmdlet 允许用户更新数据存储区中的项的值。 若要支持此 cmdlet，请覆盖[Itemcmdletprovider. Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和 Itemcmdletprovider. Setitemdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

### <a name="item-content-cmdlets"></a>项内容 cmdlet

- `Add-Content`：此 cmdlet 允许用户向项中添加内容。

- `Clear-Content`：此 cmdlet 允许用户删除项中的内容，而不会删除该项。 若要支持此 cmdlet，请覆盖[Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和 Icontentcmdletprovider. Clearcontentdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

- `Get-Content`：此 cmdlet 允许用户检索项的内容。 若要支持此 cmdlet，请覆盖[Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和 Icontentcmdletprovider. Getcontentreaderdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 [Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法返回一个[Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)接口，该接口用于定义用于读取内容的方法的定义方法的方法。

- `Set-Content`：此 cmdlet 允许用户更新项的内容。 若要支持此 cmdlet，请覆盖[Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和 Icontentcmdletprovider. Getcontentwriterdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 方法返回一个 [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 接口，该接口定义了用于写入内容的方法。

### <a name="item-property-cmdlets"></a>项属性 cmdlet

- `Clear-ItemProperty`：此 cmdlet 允许用户删除属性的值。 若要支持此 cmdlet，请覆盖[Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和 Ipropertycmdletprovider. Clearpropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。

- `Copy-ItemProperty`：此 cmdlet 允许用户将属性及其值从一个位置复制到另一个位置。 若要支持此 cmdlet，请覆盖[Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和 Idynamicpropertycmdletprovider. Copypropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法。

- `Get-ItemProperty`：此 cmdlet 检索项的属性。 若要支持此 cmdlet，请覆盖[Ipropertycmdletprovider. Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和 Ipropertycmdletprovider. Getpropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

- `Move-ItemProperty`：此 cmdlet 允许用户将属性及其值从一个位置移动到另一个位置。 若要支持此 cmdlet，请覆盖[Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和 Idynamicpropertycmdletprovider. Movepropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法。

- `New-ItemProperty`：此 cmdlet 允许用户创建新属性并设置其值。 若要支持此 cmdlet，请覆盖[Idynamicpropertycmdletprovider. Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和 Idynamicpropertycmdletprovider. Newpropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

- `Remove-ItemProperty`：此 cmdlet 允许用户删除属性及其值。 若要支持此 cmdlet，请覆盖[Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和 Idynamicpropertycmdletprovider. Removepropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

- `Rename-ItemProperty`：此 cmdlet 允许用户更改属性的名称。 若要支持此 cmdlet，请覆盖[Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和 Idynamicpropertycmdletprovider. Renamepropertydynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

- `Set-ItemProperty`：此 cmdlet 允许用户更新项的属性。 若要支持此 cmdlet，请重写[Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[Ipropertycmdletprovider。 Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法的，请重写该方法。

### <a name="location-cmdlets"></a>位置 cmdlet

- `Get-Location`：检索有关当前工作位置的信息。 无需覆盖任何方法即可支持此 cmdlet。

- `Pop-Location`：此 cmdlet 将当前位置更改为最近推入到堆栈中的位置。 无需覆盖任何方法即可支持此 cmdlet。

- `Push-Location`：此 cmdlet 将当前位置添加到位置列表（"堆栈"）的顶部。 无需覆盖任何方法即可支持此 cmdlet。

- `Set-Location`：此 cmdlet 将当前工作位置设置为指定的位置。 无需覆盖任何方法即可支持此 cmdlet。

### <a name="path-cmdlets"></a>路径 cmdlet

- `Join-Path`：此 cmdlet 允许用户合并父路径段和子路径段以创建提供程序内部路径。 若要支持此 cmdlet，请覆盖[Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

- `Convert-Path`：此 cmdlet 将路径从 Windows PowerShell 路径转换为 Windows PowerShell 提供程序路径。

- `Split-Path`：返回路径的指定部分。

- `Resolve-Path`：解析路径中的通配符，并显示路径内容。

- `Test-Path`：此 cmdlet 确定路径的所有元素是否存在。 若要支持此 cmdlet，请覆盖[Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和 Itemcmdletprovider. Itemexistsdynamicparameters 方法。 | [.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet

- `Get-PSProvider`：此 cmdlet 返回有关会话中提供的提供程序的信息。 无需覆盖任何方法即可支持此 cmdlet。