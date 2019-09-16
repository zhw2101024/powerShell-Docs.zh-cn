---
title: 提供程序类型 |Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986660"
---
# <a name="provider-types"></a>提供程序类型

提供程序通过更改 PowerShell 提供的提供程序 cmdlet 的执行操作来定义其基本功能。 例如，提供程序可以使用`Get-Item` cmdlet 的默认功能，也可以在从数据存储区中检索项时更改该 cmdlet 的操作方式。 本文档中所述的提供程序功能包括通过覆盖特定提供程序基类和接口中的方法定义的功能。

> [!NOTE]
> 有关 PowerShell 预定义的提供程序功能，请参阅[提供程序功能](/previous-versions//ee126189(v=vs.85))。

## <a name="drive-enabled-providers"></a>支持驱动器的提供程序

启用驱动器的提供程序指定用户可用的默认驱动器，并允许用户添加或删除驱动器。 在大多数情况下，提供程序是支持驱动器的提供程序，因为它们需要某些默认驱动器来访问数据存储。 但是，在编写您自己的提供程序时，您可能会或可能不希望允许用户创建和删除驱动器。

若要创建启用驱动器的提供程序，提供程序类必须派生自[DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类或派生自该类的另一个类。 **DriveCmdletProvider**类定义以下用于实现提供程序的默认驱动器并支持`New-PSDrive`和`Remove-PSDrive` cmdlet 的方法：。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，例如`NewDrive` `New-PSDrive` cmdlet 的方法，还可以覆盖`NewDriveDynamicParameters`第二种方法，例如，用于将动态参数添加到 cmdlet。

- 当使用提供程序时， [DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法将定义可供用户使用的默认驱动器。

- [DriveCmdletProvider 和 NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法是如何支持的`New-PSDrive`。提供程序 cmdlet。 此 cmdlet 允许用户创建驱动器以访问数据存储。

- [DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法定义提供程序如何支持`Remove-PSDrive`提供程序 cmdlet。 此 cmdlet 允许用户从数据存储中删除驱动器。

## <a name="item-enabled-providers"></a>启用了项目的提供程序

启用项的提供程序允许用户获取、设置或清除数据存储区中的项。 "项" 是用户可以单独访问或管理的数据存储的元素。 若要创建支持项的提供程序，提供程序类必须派生自[ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类或派生自该类的另一个类。

**ItemCmdletProvider**类定义以下用于实现特定提供程序 cmdlet 的方法。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，例如`ClearItem` `Clear-Item` cmdlet 的方法，还可以覆盖`ClearItemDynamicParameters`第二种方法，例如，用于将动态参数添加到 cmdlet。

- [ItemCmdletProvider 和 ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法是如何支持的`Clear-Item`。提供程序 cmdlet。 此 cmdlet 允许用户删除数据存储中某个项的值。

- [ItemCmdletProvider 和 GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法是如何支持的`Get-Item` 。提供程序 cmdlet。 此 cmdlet 允许用户从数据存储中检索数据。

- [ItemCmdletProvider 和 SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法是如何支持的`Set-Item` 。提供程序 cmdlet。 此 cmdlet 允许用户更新数据存储区中的项的值。

- [Itemcmdletprovider 和 InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters)`Invoke-Item`支持提供程序 cmdlet。 此 cmdlet 允许用户执行项指定的默认操作。

- [ItemCmdletProvider 和 ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法是如何支持的`Test-Path`。提供程序 cmdlet。 此 cmdlet 允许用户确定路径的所有元素是否存在。

除了用于实现提供程序 cmdlet 的方法以外， **ItemCmdletProvider**类还定义了以下方法：

- [ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)方法允许用户在指定提供程序路径时使用通配符（）。

- [ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)用于确定路径对于提供程序是否在语法和语义上是有效的。

## <a name="container-enabled-providers"></a>启用容器的提供程序

启用容器的提供程序允许用户管理容器中的项。 容器是包含公用父项下的子项的组。 若要创建启用容器的提供程序，提供程序类必须派生自[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类或派生自该类的另一个类。

> [!IMPORTANT]
> 启用容器的访问接口无法访问包含嵌套容器的数据存储区。 如果容器的子项是另一个容器，则必须实现启用导航的提供程序。

**ContainerCmdletProvider**类定义以下用于实现特定提供程序 cmdlet 的方法。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，例如`CopyItem` `Copy-Item` cmdlet 的方法，还可以覆盖`CopyItemDynamicParameters`第二种方法，例如，用于将动态参数添加到 cmdlet。

- [ContainerCmdletProvider 和 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法是如何支持的。`Copy-Item`提供程序 cmdlet。 此 cmdlet 允许用户将项从一个位置复制到另一个位置。

- [ContainerCmdletProvider 和 GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)`Get-ChildItem`支持提供程序 cmdlet。 此 cmdlet 允许用户检索父项的子项。

- [ContainerCmdletProvider 和 GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)如果指定了`Get-ChildItem` 参数，则支持`Name`提供程序 cmdlet。

- [ContainerCmdletProvider 和 NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法是如何支持的。`New-Item`提供程序 cmdlet。 此 cmdlet 允许用户在数据存储中创建新项。

- [ContainerCmdletProvider 和 RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法是如何支持的。`Remove-Item`提供程序 cmdlet。 此 cmdlet 允许用户从数据存储中删除项。

- [ContainerCmdletProvider 和 RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法是如何支持的。`Rename-Item`提供程序 cmdlet。 此 cmdlet 允许用户重命名数据存储区中的项。

除了用于实现提供程序 cmdlet 的方法以外， **ContainerCmdletProvider**类还定义了以下方法：

- 提供程序类可以使用[ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法来确定某一项是否具有子项。

- 提供程序类可以使用[ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath)方法从指定的路径创建新的特定于提供程序的路径。

## <a name="navigation-enabled-providers"></a>启用导航的提供程序

启用导航的提供程序允许用户在数据存储中移动项。 若要创建启用导航的提供程序，提供程序类必须派生自[NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

**NavigationCmdletProvider**类定义以下用于实现特定提供程序 cmdlet 的方法。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，例如`MoveItem` `Move-Item` cmdlet 的方法，还可以覆盖`MoveItemDynamicParameters`第二种方法，例如，用于将动态参数添加到 cmdlet。

- [NavigationCmdletProvider 和 MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法定义了提供程序支持的方式的方法[，这些](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法是如何支持的。`Move-Item`提供程序 cmdlet。 此 cmdlet 允许用户将项从存储区中的一个位置移到另一个位置。

- [NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法定义提供程序如何支持`Join-Path`提供程序 cmdlet。 此 cmdlet 允许用户合并父路径段和子路径段以创建提供程序内部路径。

除了用于实现提供程序 cmdlet 的方法以外， **NavigationCmdletProvider**类还定义了以下方法：

- [NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法提取路径的子节点的名称（& e）。

- [NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法会提取路径的父部分，而不是。

- [NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法决定项是否为容器项。）。 在此上下文中，容器是公共父项下的一组子项。

- [NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法将返回相对于指定基路径的项的路径，该路径为。

## <a name="content-enabled-providers"></a>启用内容的提供程序

启用内容的提供程序允许用户在数据存储中清除、获取或设置项的内容。
例如，FileSystem 提供程序允许清除、获取和设置文件系统中的文件的内容。 若要创建启用内容的提供程序，提供程序类必须实现[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的方法。

**IContentCmdletProvider**接口定义以下用于实现特定提供程序 cmdlet 的方法。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，例如`ClearContent` `Clear-Content` cmdlet 的方法，还可以覆盖`ClearContentDynamicParameters`第二种方法，例如，用于将动态参数添加到 cmdlet。

- IContentCmdletProvider 方法定义提供程序支持的方式的[ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法的定义方式的方法，它`Clear-Content`提供程序 cmdlet。 此 cmdlet 允许用户删除项的内容，而不会删除该项。

- [IContentCmdletProvider 和 GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)`Get-Content`支持提供程序 cmdlet。 此 cmdlet 允许用户检索项的内容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` 方法返回一个 [System.Management.Automation.Provider.IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) 接口，该接口定义用于读取内容的方法。

- [IContentCmdletProvider 和 GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)`Set-Content`支持提供程序 cmdlet。 此 cmdlet 允许用户更新项的内容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`方法返回一个 [System.Management.Automation.Provider.IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 接口，该接口定义用于写入内容的方法。

## <a name="property-enabled-providers"></a>启用了属性的提供程序

启用了属性的提供程序允许用户管理数据存储中项的属性。
若要创建一个启用了属性的提供程序，提供程序类必须实现[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)和 IDynamicPropertyCmdletProvider 的方法。的提供程序类 [System.Management.Automation.Provider.IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 接口。 在大多数情况下，若要支持提供程序 cmdlet，必须覆盖 PowerShell 引擎调用的方法来调用 cmdlet，如 Clear 属性 cmdlet `ClearProperty`的方法，还可以覆盖第二种方法，例如`ClearPropertyDynamicParameters`，用于将动态参数添加到 cmdlet。

**IPropertyCmdletProvider**接口定义以下用于实现特定提供程序 cmdlet 的方法：

- [IPropertyCmdletProvider 和 ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法用于定义你的提供程序的提供程序的实现方式的[方法。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)`Clear-ItemProperty`支持提供程序 cmdlet。 此 cmdlet 允许用户删除属性的值。

- IPropertyCmdletProvider 方法定义提供程序支持的方式的[GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法的定义方式的方法，它`Get-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户检索项的属性。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法定义了提供程序支持的方式的方法，该方法用于定义访问者`Set-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户更新项的属性。

  **IDynamicPropertyCmdletProvider**接口定义以下用于实现特定提供程序 cmdlet 的方法：

- [IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法用于定义你的工作方式的你的管理提供程序支持`Copy-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户将属性及其值从一个位置复制到另一个位置。

- [IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法用于定义你的工作方式的你的管理提供程序支持`Move-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户将属性及其值从一个位置移动到另一个位置。

- [IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法用于定义你的工作方式的你的管理提供程序支持`New-ItemProperty`提供程序 cmdlet。 此 cmdlet 允许用户创建新属性并设置其值。

- [IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法定义了如何进行操作的方式，以及如何你的`Remove-ItemProperty`提供程序支持 cmdlet。 此 cmdlet 允许用户删除属性及其值。

- [IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法定义了如何进行操作的方式，以及如何你的`Rename-ItemProperty`提供程序支持 cmdlet。 此 cmdlet 允许用户更改属性的名称。

## <a name="see-also"></a>另请参阅

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)
