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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853123"
---
# <a name="provider-samples"></a>提供程序示例

本部分包括访问的 Microsoft Access 数据库的提供程序的示例。 这些示例包括从所有基本提供程序类派生的提供程序类。

## <a name="in-this-section"></a>本节内容

本部分包括以下主题：

[示例 AccessDBProviderSample01](./accessdbprovidersample01.md)此示例演示如何声明直接派生的提供程序类[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类。 仅出于完整性考虑而在此处包含此项。

[AccessDBProviderSample02](./accessdbprovidersample02.md)此示例演示了如何覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法以支持对调用`New-PSDrive`和`Remove-PSDrive`cmdlet。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。

[AccessDBProviderSample03](./accessdbprovidersample03.md)此示例演示了如何覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法以支持对调用`Get-Item`和`Set-Item`cmdlet。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

[AccessDBProviderSample04](./accessdbprovidersample04.md)此示例演示了如何覆盖容器方法，以支持对调用`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。

[AccessDBProviderSample05](./accessdbprovidersample05.md)此示例演示了如何覆盖容器方法，以支持对调用`Move-Item`和`Join-Path`cmdlet。 当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

[AccessDBProviderSample06](./accessdbprovidersample06.md)此示例演示了如何覆盖内容方法以支持对调用`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。 当用户需要管理数据存储区中的项的内容时，应实现这些方法。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并实现[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)