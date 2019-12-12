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
# <a name="accessdbprovidersample04"></a><span data-ttu-id="872e3-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="872e3-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="872e3-103">此示例演示如何覆盖容器方法以支持对 `Copy-Item`、`Get-ChildItem`、`New-Item`和 `Remove-Item` cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="872e3-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="872e3-104">当数据存储区包含属于容器的项时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="872e3-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="872e3-105">容器是包含公用父项下的子项的组。</span><span class="sxs-lookup"><span data-stu-id="872e3-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="872e3-106">此示例中的提供程序类派生自[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="872e3-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="872e3-107">说明</span><span class="sxs-lookup"><span data-stu-id="872e3-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="872e3-108">你的提供程序类最有可能派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="872e3-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="872e3-109">本示例演示下面几点：</span><span class="sxs-lookup"><span data-stu-id="872e3-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="872e3-110">声明 `CmdletProvider` 特性。</span><span class="sxs-lookup"><span data-stu-id="872e3-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="872e3-111">定义一个派生自[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="872e3-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="872e3-112">覆盖[ContainerCmdletProvider 的 CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以更改 `Copy-Item` cmdlet 的行为，该行为允许用户将项从一个位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="872e3-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="872e3-113">（此示例不显示如何将动态参数添加到 `Copy-Item` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="872e3-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="872e3-114">覆盖[Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以更改 ChildItems cmdlet 的行为，该行为允许用户检索父项的子项目。 Containercmdletprovider）的行为。</span><span class="sxs-lookup"><span data-stu-id="872e3-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="872e3-115">（此示例不显示如何向 ChildItems cmdlet 添加动态参数。）</span><span class="sxs-lookup"><span data-stu-id="872e3-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="872e3-116">当指定 cmdlet 的 `Name` 参数时，将覆盖[Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以更改 ChildItems cmdlet 的行为的行为方式。</span><span class="sxs-lookup"><span data-stu-id="872e3-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="872e3-117">覆盖[Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以更改 `New-Item` cmdlet 的行为，该行为允许用户向数据存储区中添加项的行为。</span><span class="sxs-lookup"><span data-stu-id="872e3-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="872e3-118">（此示例不显示如何将动态参数添加到 `New-Item` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="872e3-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="872e3-119">覆盖[Containercmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以更改 `Remove-Item` cmdlet 的行为方式。</span><span class="sxs-lookup"><span data-stu-id="872e3-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="872e3-120">（此示例不显示如何将动态参数添加到 `Remove-Item` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="872e3-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="872e3-121">示例</span><span class="sxs-lookup"><span data-stu-id="872e3-121">Example</span></span>

<span data-ttu-id="872e3-122">此示例演示如何覆盖复制、创建和删除项所需的方法，以及用于获取父项的子项的方法。</span><span class="sxs-lookup"><span data-stu-id="872e3-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="872e3-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="872e3-123">See Also</span></span>

[<span data-ttu-id="872e3-124">"Itemcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="872e3-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="872e3-125">"Containercmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="872e3-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="872e3-126">"Navigationcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="872e3-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="872e3-127">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="872e3-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
