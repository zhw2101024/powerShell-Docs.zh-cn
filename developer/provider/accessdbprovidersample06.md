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
ms.openlocfilehash: 59832ed8a4fad3b07a171946bff28fb3e1dbe442
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854653"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="ad30f-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="ad30f-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="ad30f-103">此示例演示了如何覆盖内容方法以支持对调用`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad30f-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="ad30f-104">当用户需要管理数据存储区中的项的内容时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="ad30f-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="ad30f-105">在此示例中的提供程序类派生[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并实现[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。</span><span class="sxs-lookup"><span data-stu-id="ad30f-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ad30f-106">说明</span><span class="sxs-lookup"><span data-stu-id="ad30f-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad30f-107">提供程序类将很可能从以下类之一派生，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="ad30f-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="ad30f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="ad30f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="ad30f-109">请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="ad30f-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="ad30f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="ad30f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="ad30f-111">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="ad30f-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="ad30f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="ad30f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="ad30f-113">有关选择哪个提供程序类派生自基于提供程序功能，请参阅详细信息[设计你 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ad30f-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="ad30f-114">此示例将演示如下：</span><span class="sxs-lookup"><span data-stu-id="ad30f-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="ad30f-115">声明`CmdletProvider`属性。</span><span class="sxs-lookup"><span data-stu-id="ad30f-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="ad30f-116">定义提供程序类派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，声明[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。</span><span class="sxs-lookup"><span data-stu-id="ad30f-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="ad30f-117">覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，若要更改的行为`Clear-Content`cmdlet，从而允许用户从一个项中删除的内容。</span><span class="sxs-lookup"><span data-stu-id="ad30f-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="ad30f-118">(此示例不会显示如何添加将动态参数为`Clear-Content`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="ad30f-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="ad30f-119">覆盖[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，若要更改的行为`Get-Content`cmdlet，从而允许用户检索其内容的项。</span><span class="sxs-lookup"><span data-stu-id="ad30f-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="ad30f-120">(此示例不会显示如何添加将动态参数为`Get-Content`cmdlet。)。</span><span class="sxs-lookup"><span data-stu-id="ad30f-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="ad30f-121">覆盖[Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，若要更改的行为`Set-Content`cmdlet，从而允许用户更新项的内容。</span><span class="sxs-lookup"><span data-stu-id="ad30f-121">Overwriting the [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="ad30f-122">(此示例不会显示如何添加将动态参数为`Set-Content`cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="ad30f-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="ad30f-123">示例</span><span class="sxs-lookup"><span data-stu-id="ad30f-123">Example</span></span>

<span data-ttu-id="ad30f-124">此示例演示如何覆盖清除、 获取和设置 Microsoft Access 数据中的各项的内容基础所需的方法。</span><span class="sxs-lookup"><span data-stu-id="ad30f-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="ad30f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad30f-125">See Also</span></span>

[<span data-ttu-id="ad30f-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ad30f-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="ad30f-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ad30f-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="ad30f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ad30f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="ad30f-129">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="ad30f-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)