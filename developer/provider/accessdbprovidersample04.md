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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057614"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="2e198-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="2e198-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="2e198-103">此示例演示了如何覆盖容器方法，以支持对调用`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e198-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="2e198-104">当数据存储区包含属于容器的项时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="2e198-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="2e198-105">容器是包含公用父项下的子项的组。</span><span class="sxs-lookup"><span data-stu-id="2e198-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="2e198-106">在此示例中的提供程序类派生[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="2e198-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2e198-107">说明</span><span class="sxs-lookup"><span data-stu-id="2e198-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e198-108">提供程序类将很可能派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="2e198-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="2e198-109">此示例将演示如下：</span><span class="sxs-lookup"><span data-stu-id="2e198-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="2e198-110">声明`CmdletProvider`属性。</span><span class="sxs-lookup"><span data-stu-id="2e198-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="2e198-111">定义提供程序类派生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="2e198-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="2e198-112">覆盖[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，若要更改的行为`Copy-Item`这样用户就可以将项从一个位置复制到另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e198-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="2e198-113">(此示例不会显示如何添加将动态参数为`Copy-Item`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="2e198-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="2e198-114">覆盖[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以更改 Get ChildItems cmdlet，这样用户就可以检索父项的子项的行为.</span><span class="sxs-lookup"><span data-stu-id="2e198-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="2e198-115">（此示例不显示如何将动态参数添加到 Get ChildItems cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="2e198-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="2e198-116">覆盖[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以更改 Get ChildItems cmdlet 的行为时`Name`指定 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="2e198-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="2e198-117">覆盖[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，若要更改的行为`New-Item`cmdlet，这样用户就可以将项添加到数据存储。</span><span class="sxs-lookup"><span data-stu-id="2e198-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="2e198-118">(此示例不会显示如何添加将动态参数为`New-Item`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="2e198-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="2e198-119">覆盖[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，若要更改的行为`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e198-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="2e198-120">(此示例不会显示如何添加将动态参数为`Remove-Item`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="2e198-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="2e198-121">示例</span><span class="sxs-lookup"><span data-stu-id="2e198-121">Example</span></span>

<span data-ttu-id="2e198-122">此示例演示如何覆盖复制、 创建和删除项，以及用于获取项的父项的子级的方法所需的方法。</span><span class="sxs-lookup"><span data-stu-id="2e198-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="2e198-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e198-123">See Also</span></span>

[<span data-ttu-id="2e198-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2e198-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="2e198-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2e198-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="2e198-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2e198-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="2e198-127">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="2e198-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)