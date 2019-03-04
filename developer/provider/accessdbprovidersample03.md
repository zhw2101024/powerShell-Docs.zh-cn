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
# <a name="accessdbprovidersample03"></a><span data-ttu-id="384e1-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="384e1-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="384e1-103">此示例演示了如何覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)并[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法以支持对调用`Get-Item`和`Set-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="384e1-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="384e1-104">在此示例中的提供程序类派生[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="384e1-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="384e1-105">说明</span><span class="sxs-lookup"><span data-stu-id="384e1-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="384e1-106">提供程序类将很可能从以下类之一派生，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="384e1-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="384e1-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="384e1-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="384e1-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="384e1-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="384e1-109">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="384e1-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="384e1-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="384e1-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="384e1-111">请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="384e1-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="384e1-112">有关选择哪个提供程序类派生自基于提供程序功能，请参阅详细信息[设计你 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="384e1-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="384e1-113">此示例将演示如下：</span><span class="sxs-lookup"><span data-stu-id="384e1-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="384e1-114">声明`CmdletProvider`属性。</span><span class="sxs-lookup"><span data-stu-id="384e1-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="384e1-115">定义提供程序类派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="384e1-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="384e1-116">覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，若要更改的行为`New-PSDrive`cmdlet，从而允许用户创建新的驱动器。</span><span class="sxs-lookup"><span data-stu-id="384e1-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="384e1-117">(此示例不会显示如何添加将动态参数为`New-PSDrive`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="384e1-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="384e1-118">覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支持删除现有的驱动器。</span><span class="sxs-lookup"><span data-stu-id="384e1-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="384e1-119">覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，若要更改的行为`Get-Item`cmdlet，从而允许用户从数据存储区中检索项。</span><span class="sxs-lookup"><span data-stu-id="384e1-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="384e1-120">(此示例不会显示如何添加将动态参数为`Get-Item`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="384e1-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="384e1-121">覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，若要更改的行为`Set-Item`cmdlet，从而允许用户更新数据存储区中的项。</span><span class="sxs-lookup"><span data-stu-id="384e1-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="384e1-122">(此示例不会显示如何添加将动态参数为`Get-Item`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="384e1-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="384e1-123">覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，若要更改的行为`Test-Path`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="384e1-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="384e1-124">(此示例不会显示如何添加将动态参数为`Test-Path`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="384e1-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="384e1-125">覆盖[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以确定提供的路径是否有效。</span><span class="sxs-lookup"><span data-stu-id="384e1-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="384e1-126">示例</span><span class="sxs-lookup"><span data-stu-id="384e1-126">Example</span></span>

<span data-ttu-id="384e1-127">此示例演示如何覆盖所需获取和设置 Microsoft Access 数据中的项基本的方法。</span><span class="sxs-lookup"><span data-stu-id="384e1-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="384e1-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="384e1-128">See Also</span></span>

[<span data-ttu-id="384e1-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="384e1-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="384e1-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="384e1-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="384e1-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="384e1-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="384e1-132">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="384e1-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)