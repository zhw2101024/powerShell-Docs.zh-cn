---
title: AccessDBProviderSample06 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366326"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

此示例演示如何覆盖内容方法以支持对 `Clear-Content`、`Get-Content`和 `Set-Content` cmdlet 的调用。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 此示例中的提供程序类派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并且它实现了[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的执行程序。）。

## <a name="demonstrates"></a>说明

> [!IMPORTANT]
> 提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：
>
> -   " [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。 请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   " [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。 请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   " [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。
>
> 有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。

本示例演示下面几点：

- 声明 `CmdletProvider` 特性。

- 定义一个派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类的提供程序类，并声明一个声明[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的提供程序类。

- 覆盖[Icontentcmdletprovider 的 Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以更改 `Clear-Content` cmdlet 的行为，从而允许用户从项中删除该内容。 （此示例不显示如何将动态参数添加到 `Clear-Content` cmdlet。）

- 覆盖[Icontentcmdletprovider 的 Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以更改 `Get-Content` cmdlet 的行为，从而允许用户检索项的内容的内容。 （此示例不显示如何将动态参数添加到 `Get-Content` cmdlet。）。

- 覆盖[Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以更改 `Set-Content` cmdlet 的行为，从而使用户能够更新项的内容了。 （此示例不显示如何将动态参数添加到 `Set-Content` cmdlet。）

## <a name="example"></a>示例

此示例演示如何覆盖清除、获取和设置 Microsoft Access 数据库中项的内容所需的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>另请参阅

["Itemcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

["Containercmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

["Navigationcmdletprovider"。](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计你的 Windows PowerShell 提供程序](./provider-types.md)
