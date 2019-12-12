---
title: AccessDBProviderSample04 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366336"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

此示例演示如何覆盖容器方法以支持对 `Copy-Item`、`Get-ChildItem`、`New-Item`和 `Remove-Item` cmdlet 的调用。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 此示例中的提供程序类派生自[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。

## <a name="demonstrates"></a>说明

> [!IMPORTANT]
> 你的提供程序类最有可能派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

本示例演示下面几点：

- 声明 `CmdletProvider` 特性。

- 定义一个派生自[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类的提供程序类。

- 覆盖[ContainerCmdletProvider 的 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以更改 `Copy-Item` cmdlet 的行为，该行为允许用户将项从一个位置复制到另一个位置。 （此示例不显示如何将动态参数添加到 `Copy-Item` cmdlet。）

- 覆盖[Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以更改 ChildItems cmdlet 的行为，该行为允许用户检索父项的子项目。 Containercmdletprovider）的行为。 （此示例不显示如何向 ChildItems cmdlet 添加动态参数。）

- 当指定 cmdlet 的 `Name` 参数时，将覆盖[Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以更改 ChildItems cmdlet 的行为的行为方式。

- 覆盖[Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以更改 `New-Item` cmdlet 的行为，该行为允许用户向数据存储区中添加项的行为。 （此示例不显示如何将动态参数添加到 `New-Item` cmdlet。）

- 覆盖[Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以更改 `Remove-Item` cmdlet 的行为方式。 （此示例不显示如何将动态参数添加到 `Remove-Item` cmdlet。）

## <a name="example"></a>示例

此示例演示如何覆盖复制、创建和删除项所需的方法，以及用于获取父项的子项的方法。

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另请参阅

["Itemcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

["Containercmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

["Navigationcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计你的 Windows PowerShell 提供程序](./provider-types.md)
