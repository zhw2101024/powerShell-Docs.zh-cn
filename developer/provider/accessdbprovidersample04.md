---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856693"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

此示例演示了如何覆盖容器方法，以支持对调用`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。 当数据存储区包含属于容器的项时，应实现这些方法。 容器是包含公用父项下的子项的组。 在此示例中的提供程序类派生[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。

## <a name="demonstrates"></a>说明

> [!IMPORTANT]
> 提供程序类将很可能派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

此示例将演示如下：

- 声明`CmdletProvider`属性。

- 定义提供程序类派生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。

- 覆盖[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，若要更改的行为`Copy-Item`这样用户就可以将项从一个位置复制到另一个 cmdlet。 (此示例不会显示如何添加将动态参数为`Copy-Item`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以更改 Get ChildItems cmdlet，这样用户就可以检索父项的子项的行为. （此示例不显示如何将动态参数添加到 Get ChildItems cmdlet）。

- 覆盖[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以更改 Get ChildItems cmdlet 的行为时`Name`指定 cmdlet 参数。

- 覆盖[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，若要更改的行为`New-Item`cmdlet，这样用户就可以将项添加到数据存储。 (此示例不会显示如何添加将动态参数为`New-Item`cmdlet。)

- 覆盖[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，若要更改的行为`Remove-Item`cmdlet。 (此示例不会显示如何添加将动态参数为`Remove-Item`cmdlet。)

## <a name="example"></a>示例

此示例演示如何覆盖复制、 创建和删除项，以及用于获取项的父项的子级的方法所需的方法。

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计 Windows PowerShell 提供程序](./provider-types.md)