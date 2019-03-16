---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055540"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

此示例演示了如何覆盖内容方法以支持对调用`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并实现[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。

## <a name="demonstrates"></a>说明

> [!IMPORTANT]
> 提供程序类将很可能从以下类之一派生，并可能实现其他提供程序接口：
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。 请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。 请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。
>
> 有关选择哪个提供程序类派生自基于提供程序功能，请参阅详细信息[设计你 Windows PowerShell 提供程序](./provider-types.md)。

此示例将演示如下：

- 声明`CmdletProvider`属性。

- 定义提供程序类派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，声明[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。

- 覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，若要更改的行为`Clear-Content`cmdlet，从而允许用户从一个项中删除的内容。 (此示例不会显示如何添加将动态参数为`Clear-Content`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，若要更改的行为`Get-Content`cmdlet，从而允许用户检索其内容的项。 (此示例不会显示如何添加将动态参数为`Get-Content`cmdlet。)。

- 覆盖[Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，若要更改的行为`Set-Content`cmdlet，从而允许用户更新项的内容。 (此示例不会显示如何添加将动态参数为`Set-Content`cmdlet。)

## <a name="example"></a>示例

此示例演示如何覆盖清除、 获取和设置 Microsoft Access 数据中的各项的内容基础所需的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计 Windows PowerShell 提供程序](./provider-types.md)