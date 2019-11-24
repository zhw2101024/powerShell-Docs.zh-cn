---
title: AccessDBProviderSample03 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359986"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

此示例演示如何覆盖[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支持对 `Get-Item` 和 `Set-Item` cmdlet 的调用的调用，这种情况下是如此。 此示例中的提供程序类派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

## <a name="demonstrates"></a>示例

> [!IMPORTANT]
> 提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：
>
> -   " [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。
> -   " [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。 请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   " [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。 请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。

此示例演示了以下内容：

- 声明 `CmdletProvider` 特性。

- 定义一个派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类的提供程序类。

- 覆盖[Drivecmdletprovider 的 Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以更改 `New-PSDrive` cmdlet 的行为，从而允许用户创建新的驱动器。 （此示例不显示如何将动态参数添加到 `New-PSDrive` cmdlet。）

- 覆盖[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持删除现有驱动器。

- 覆盖[Itemcmdletprovider 的 Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以更改 `Get-Item` cmdlet 的行为，从而允许用户从数据存储中检索项。 （此示例不显示如何将动态参数添加到 `Get-Item` cmdlet。）

- 覆盖[Itemcmdletprovider 的 Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以更改 `Set-Item` cmdlet 的行为，从而使用户能够更新数据存储中的项。 （此示例不显示如何将动态参数添加到 `Get-Item` cmdlet。）

- 覆盖[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以更改 `Test-Path` cmdlet 的行为方式。 （此示例不显示如何将动态参数添加到 `Test-Path` cmdlet。）

- 覆盖[Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以确定提供的路径是否有效。

## <a name="example"></a>示例

此示例演示如何覆盖获取和设置 Microsoft Access 数据库中的项所需的方法。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>另请参阅

["Itemcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

["Containercmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

["Navigationcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计你的 Windows PowerShell 提供程序](./provider-types.md)
