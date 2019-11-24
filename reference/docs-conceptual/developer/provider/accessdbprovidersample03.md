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
# <a name="accessdbprovidersample03"></a><span data-ttu-id="96f63-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="96f63-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="96f63-103">此示例演示如何覆盖[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[Itemcmdletprovider. Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支持对 `Get-Item` 和 `Set-Item` cmdlet 的调用的调用，这种情况下是如此。</span><span class="sxs-lookup"><span data-stu-id="96f63-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="96f63-104">此示例中的提供程序类派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="96f63-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="96f63-105">示例</span><span class="sxs-lookup"><span data-stu-id="96f63-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96f63-106">提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="96f63-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="96f63-107">" [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="96f63-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="96f63-108">" [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="96f63-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="96f63-109">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="96f63-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="96f63-110">" [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="96f63-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="96f63-111">请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="96f63-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="96f63-112">有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="96f63-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="96f63-113">此示例演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="96f63-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="96f63-114">声明 `CmdletProvider` 特性。</span><span class="sxs-lookup"><span data-stu-id="96f63-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="96f63-115">定义一个派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="96f63-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="96f63-116">覆盖[Drivecmdletprovider 的 Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以更改 `New-PSDrive` cmdlet 的行为，从而允许用户创建新的驱动器。</span><span class="sxs-lookup"><span data-stu-id="96f63-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="96f63-117">（此示例不显示如何将动态参数添加到 `New-PSDrive` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="96f63-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="96f63-118">覆盖[Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持删除现有驱动器。</span><span class="sxs-lookup"><span data-stu-id="96f63-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="96f63-119">覆盖[Itemcmdletprovider 的 Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以更改 `Get-Item` cmdlet 的行为，从而允许用户从数据存储中检索项。</span><span class="sxs-lookup"><span data-stu-id="96f63-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="96f63-120">（此示例不显示如何将动态参数添加到 `Get-Item` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="96f63-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="96f63-121">覆盖[Itemcmdletprovider 的 Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以更改 `Set-Item` cmdlet 的行为，从而使用户能够更新数据存储中的项。</span><span class="sxs-lookup"><span data-stu-id="96f63-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="96f63-122">（此示例不显示如何将动态参数添加到 `Get-Item` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="96f63-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="96f63-123">覆盖[Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以更改 `Test-Path` cmdlet 的行为方式。</span><span class="sxs-lookup"><span data-stu-id="96f63-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="96f63-124">（此示例不显示如何将动态参数添加到 `Test-Path` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="96f63-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="96f63-125">覆盖[Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以确定提供的路径是否有效。</span><span class="sxs-lookup"><span data-stu-id="96f63-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="96f63-126">示例</span><span class="sxs-lookup"><span data-stu-id="96f63-126">Example</span></span>

<span data-ttu-id="96f63-127">此示例演示如何覆盖获取和设置 Microsoft Access 数据库中的项所需的方法。</span><span class="sxs-lookup"><span data-stu-id="96f63-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="96f63-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96f63-128">See Also</span></span>

[<span data-ttu-id="96f63-129">"Itemcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="96f63-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="96f63-130">"Containercmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="96f63-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="96f63-131">"Navigationcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="96f63-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="96f63-132">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="96f63-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
