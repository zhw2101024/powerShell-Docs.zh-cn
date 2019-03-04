---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859403"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

此示例演示了如何覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)并[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法以支持对调用`Get-Item`和`Set-Item`cmdlet。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

## <a name="demonstrates"></a>说明

> [!IMPORTANT]
> 提供程序类将很可能从以下类之一派生，并可能实现其他提供程序接口：
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。 请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。 请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 有关选择哪个提供程序类派生自基于提供程序功能，请参阅详细信息[设计你 Windows PowerShell 提供程序](./provider-types.md)。

此示例将演示如下：

- 声明`CmdletProvider`属性。

- 定义提供程序类派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

- 覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，若要更改的行为`New-PSDrive`cmdlet，从而允许用户创建新的驱动器。 (此示例不会显示如何添加将动态参数为`New-PSDrive`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持删除现有的驱动器。

- 覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，若要更改的行为`Get-Item`cmdlet，从而允许用户从数据存储区中检索项。 (此示例不会显示如何添加将动态参数为`Get-Item`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，若要更改的行为`Set-Item`cmdlet，从而允许用户更新数据存储区中的项。 (此示例不会显示如何添加将动态参数为`Get-Item`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，若要更改的行为`Test-Path`cmdlet。 (此示例不会显示如何添加将动态参数为`Test-Path`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以确定提供的路径是否有效。

## <a name="example"></a>示例

此示例演示如何覆盖所需获取和设置 Microsoft Access 数据中的项基本的方法。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计 Windows PowerShell 提供程序](./provider-types.md)