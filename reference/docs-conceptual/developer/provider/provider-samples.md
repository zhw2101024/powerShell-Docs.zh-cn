---
title: 提供程序示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366296"
---
# <a name="provider-samples"></a>提供程序示例

本部分包含访问 Microsoft Access 数据库的访问接口的示例。 这些示例包括派生自所有基提供程序类的提供程序类。

## <a name="in-this-section"></a>本部分内容

本部分包括以下主题：

[AccessDBProviderSample01 示例](./accessdbprovidersample01.md)此示例显示了如何声明直接从[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类派生的提供程序类。 仅出于完整性考虑而在此处包含此项。

[AccessDBProviderSample02](./accessdbprovidersample02.md)此示例演示如何覆盖[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持对 `New-PSDrive` 和 `Remove-PSDrive` cmdlet 的调用的调用，这种情况下是如此。 此示例中的提供程序类派生自[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。

[AccessDBProviderSample03](./accessdbprovidersample03.md)此示例演示如何覆盖[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支持对 `Get-Item` 和 `Set-Item` cmdlet 的调用的调用，这种情况下是如此。 此示例中的提供程序类派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

[AccessDBProviderSample04](./accessdbprovidersample04.md)此示例演示如何覆盖容器方法以支持对 `Copy-Item`、`Get-ChildItem`、`New-Item`和 `Remove-Item` cmdlet 的调用。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 此示例中的提供程序类派生自[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。

[AccessDBProviderSample05](./accessdbprovidersample05.md)此示例演示如何覆盖容器方法以支持对 `Move-Item` 和 `Join-Path` cmdlet 的调用。 当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。 此示例中的提供程序类派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

[AccessDBProviderSample06](./accessdbprovidersample06.md)此示例演示如何覆盖内容方法以支持对 `Clear-Content`、`Get-Content`和 `Set-Content` cmdlet 的调用。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 此示例中的提供程序类派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并且它实现了[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的执行程序。）。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)