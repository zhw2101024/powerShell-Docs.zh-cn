---
title: 提供程序类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 25b604621c90f1aa88bc1eea365e47db66e98c3d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858403"
---
# <a name="provider-types"></a>提供程序类型

提供程序通过更改提供程序 cmdlet （由 Windows PowerShell） 执行其操作的方式定义其基本功能。 例如，提供程序可以使用的默认功能`Get-Item`cmdlet，或者他们可以更改从数据存储区中检索项时，该 cmdlet 的运行方式。 本主题中所述的提供程序功能包括通过覆盖从特定的提供程序基类和接口的方法定义的功能。

> [!NOTE]
> 有关预定义的 Windows PowerShell 提供程序功能，请参阅[提供程序的功能](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6)。

## <a name="drive-enabled-providers"></a>启用驱动器的提供程序

启用驱动器的提供程序指定向用户提供的默认驱动器，并允许用户添加或删除驱动器。 在大多数情况下，提供程序是已启用驱动器的提供程序，因为它们需要一些默认的驱动器来访问数据存储区。 但是，编写自己的提供程序时您可能会或可能不希望允许用户创建和删除驱动器。

若要创建驱动器启用提供程序，提供程序类必须派生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类或派生自该类的另一个类。 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类定义以下方法用来实现的提供程序的默认驱动器和支持`New-PSDrive`和`Remove-PSDrive`cmdlet。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`NewDrive`方法`New-PSDrive`cmdlet，并 （可选） 你可以覆盖之类的第二个方法`NewDriveDynamicParameters`，用于将动态参数添加到该 cmdlet。

- [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法定义可供用户使用的提供程序时的默认驱动器。

- [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)并[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法定义您的提供程序如何支持`New-PSDrive`提供程序 cmdlet。 此 cmdlet 允许用户创建的驱动器访问数据存储区。

- [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法定义您的提供程序如何支持`Remove-PSDrive`提供程序 cmdlet。 此 cmdlet 允许用户从数据存储区中删除驱动器。

## <a name="item-enabled-providers"></a>启用了项的提供程序

启用了项的提供程序允许用户获取、 设置或清除数据存储区中的项。 "项"是用户可以访问或独立管理的数据存储区的一个元素。 若要创建的项启用提供程序，提供程序类必须派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类或派生自该类的另一个类。

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类定义以下方法用于实现特定的提供程序 cmdlet。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`ClearItem`方法`Clear-Item`cmdlet，并 （可选） 你可以覆盖之类的第二个方法`ClearItemDynamicParameters`，用于将动态参数添加到该 cmdlet。

- [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)并[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法定义您的提供程序如何支持`Clear-Item`提供程序 cmdlet。 此 cmdlet 允许用户删除的数据存储区中项的值。

- [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)并[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法定义如何您的提供程序支持`Get-Item`提供程序 cmdlet。 此 cmdlet 允许用户从数据存储中检索数据。

- [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)并[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法定义如何您的提供程序支持`Set-Item`提供程序 cmdlet。 此 cmdlet 允许用户更新的数据存储区中的项的值。

- [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)并[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法定义您的提供程序如何支持`Invoke-Item`提供程序 cmdlet。 此 cmdlet 允许用户执行指定的项的默认操作。

- [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)并[System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法定义您的提供程序如何支持`Test-Path`提供程序 cmdlet。 此 cmdlet 允许用户确定路径的所有元素是否都存在。

  方法可用来实现提供程序 cmdlet，除了[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类还定义了以下方法：

- [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)方法，则允许用户指定的提供程序路径时使用通配符。

- [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)用于确定的路径是语法和语义上有效的提供程序。

## <a name="container-enabled-providers"></a>启用容器的提供程序

启用容器的提供程序允许用户管理是容器的项。 容器是包含公用父项下的子项的组。 若要创建启用了容器的提供程序，提供程序类必须派生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类或派生自该类的另一个类。

> [!IMPORTANT]
> 启用容器的提供程序无法访问数据存储区，其中包含嵌套的容器。 如果容器的子项目是另一个容器，则必须实现导航启用提供程序。

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类定义以下方法用于实现特定的提供程序 cmdlet。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`CopyItem`方法`Copy-Item`cmdlet，并 （可选） 你可以覆盖之类的第二个方法`CopyItemDynamicParameters`，用于将动态参数添加到该 cmdlet。

- [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)并[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法定义您的提供程序如何支持`Copy-Item`提供程序 cmdlet。 此 cmdlet 允许用户将项从一个位置复制到另一个。

- [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)和[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法定义您的提供程序如何支持`Get-ChildItem`提供程序 cmdlet。 此 cmdlet 允许用户检索父项的子项。

- [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)和[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法定义您的提供程序如何支持`Get-ChildItem`提供程序 cmdlet 如果其`Name`指定参数。

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)并[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法定义您的提供程序如何支持`New-Item`提供程序 cmdlet。 此 cmdlet 允许用户在数据存储区中创建新项目。

- [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)并[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法定义您的提供程序如何支持`Remove-Item`提供程序 cmdlet。 此 cmdlet 允许用户从数据存储区中删除项目。

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)并[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法定义您的提供程序如何支持`Rename-Item`提供程序 cmdlet。 此 cmdlet 允许用户重命名数据存储中的项目。

  方法可用来实现提供程序 cmdlet，除了[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类还定义了以下方法：

- [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法可以使用由提供程序类，以确定某个项是否有子项目。

- [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath)方法可以由提供程序类以从指定的路径创建新的特定于提供程序的路径。

## <a name="navigation-enabled-providers"></a>启用导航的提供程序

启用导航的提供程序允许用户在数据存储区中移动项。 若要创建启用了导航提供程序，提供程序类必须派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类定义以下方法用于实现特定的提供程序 cmdlet。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`MoveItem`方法`Move-Item`cmdlet，并 （可选） 你可以覆盖之类的第二个方法`MoveItemDynamicParameters`，用于将动态参数添加到该 cmdlet。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)并[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法定义您的提供程序如何支持`Move-Item`提供程序 cmdlet。 此 cmdlet 允许用户将项从存储区中的一个位置移动到另一个位置。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法定义您的提供程序如何支持`Join-Path`提供程序 cmdlet。 此 cmdlet 允许用户以合并一个父级和子级路径片段来创建提供程序内部的路径。

  方法可用来实现提供程序 cmdlet，除了[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类还定义了以下方法：

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法提取一个路径的子节点的名称。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法提取路径的父部件。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法确定项是否为容器项。 在此上下文中，容器是包含公用父项下的子项的组。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法返回的路径是相对于指定的基路径的项。

## <a name="content-enabled-providers"></a>启用了内容的提供程序

启用了内容的提供程序允许用户以清除、 获取或设置数据存储区中的各项的内容。 例如，FileSystem 提供程序，可清除、 获取和设置文件系统中的文件的内容。 若要创建的内容已启用提供程序，提供程序类必须实现的方法[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口定义用于实现特定的提供程序 cmdlet 的以下方法。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`ClearContent`方法`Clear-Content`cmdlet，并 （可选） 你可以覆盖之类的第二个方法`ClearContentDynamicParameters`，用于将动态参数添加到该 cmdlet。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法定义您的提供程序如何支持`Clear-Content`提供程序 cmdlet。 此 cmdlet 允许用户删除项的内容，而不删除该项。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法定义您的提供程序如何支持`Get-Content`提供程序 cmdlet。 此 cmdlet 允许用户检索其内容的项。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法将返回[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)定义接口用于读取内容的方法。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法定义您的提供程序如何支持`Set-Content`提供程序 cmdlet。 此 cmdlet 允许用户更新项的内容。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法将返回[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)定义接口用于写入内容的方法。

## <a name="property-enabled-providers"></a>属性启用提供程序

属性启用提供程序允许用户管理的数据存储区中的项的属性。 若要创建启用了属性的提供程序，提供程序类必须实现的方法[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)接口。 在大多数情况下，若要支持提供程序 cmdlet 必须覆盖方法，用于 Windows PowerShell 引擎调用以调用 cmdlet，如`ClearProperty`清除属性 cmdlet，并选择性地将您的方法可以覆盖之类的第二个方法`ClearPropertyDynamicParameters`，用于将动态参数添加到该 cmdlet。

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口定义用于实现特定的提供程序 cmdlet 的以下方法：

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法定义您的提供程序如何支持`Clear-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户删除属性的值。

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法定义您的提供程序如何支持`Get-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户检索其属性的项。

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法定义您的提供程序如何支持`Set-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户更新项的属性。

  [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)接口定义用于实现特定的提供程序 cmdlet 的以下方法：

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法定义您的提供程序如何支持`Copy-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户将属性和其值从一个位置复制到另一个。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法定义您的提供程序如何支持`Move-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户将属性和其值从一个位置移到另一个。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法定义您的提供程序如何支持`New-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户创建新的属性并将其值设置。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法定义您的提供程序如何支持`Remove-ItemProperty`cmdlet。 此 cmdlet 允许用户删除一个属性及其值。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法定义您的提供程序如何支持`Rename-ItemProperty`cmdlet。 此 cmdlet 允许用户更改的属性名称。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)