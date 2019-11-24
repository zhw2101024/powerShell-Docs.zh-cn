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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366326"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="b3158-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="b3158-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="b3158-103">此示例演示如何覆盖内容方法以支持对 `Clear-Content`、`Get-Content`和 `Set-Content` cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="b3158-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="b3158-104">当用户需要管理数据存储区中的项的内容时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="b3158-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="b3158-105">此示例中的提供程序类派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并且它实现了[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的执行程序。）。</span><span class="sxs-lookup"><span data-stu-id="b3158-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b3158-106">示例</span><span class="sxs-lookup"><span data-stu-id="b3158-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3158-107">提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="b3158-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="b3158-108">" [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="b3158-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b3158-109">请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="b3158-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="b3158-110">" [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="b3158-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b3158-111">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="b3158-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="b3158-112">" [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="b3158-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="b3158-113">有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b3158-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b3158-114">此示例演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="b3158-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b3158-115">声明 `CmdletProvider` 特性。</span><span class="sxs-lookup"><span data-stu-id="b3158-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b3158-116">定义一个派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类的提供程序类，并声明一个声明[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="b3158-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="b3158-117">覆盖[Icontentcmdletprovider 的 Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以更改 `Clear-Content` cmdlet 的行为，从而允许用户从项中删除该内容。</span><span class="sxs-lookup"><span data-stu-id="b3158-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="b3158-118">（此示例不显示如何将动态参数添加到 `Clear-Content` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="b3158-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="b3158-119">覆盖[Icontentcmdletprovider 的 Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以更改 `Get-Content` cmdlet 的行为，从而允许用户检索项的内容的内容。</span><span class="sxs-lookup"><span data-stu-id="b3158-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="b3158-120">（此示例不显示如何将动态参数添加到 `Get-Content` cmdlet。）。</span><span class="sxs-lookup"><span data-stu-id="b3158-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="b3158-121">覆盖[Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以更改 `Set-Content` cmdlet 的行为，从而使用户能够更新项的内容了。</span><span class="sxs-lookup"><span data-stu-id="b3158-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="b3158-122">（此示例不显示如何将动态参数添加到 `Set-Content` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="b3158-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="b3158-123">示例</span><span class="sxs-lookup"><span data-stu-id="b3158-123">Example</span></span>

<span data-ttu-id="b3158-124">此示例演示如何覆盖清除、获取和设置 Microsoft Access 数据库中项的内容所需的方法。</span><span class="sxs-lookup"><span data-stu-id="b3158-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="b3158-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3158-125">See Also</span></span>

[<span data-ttu-id="b3158-126">"Itemcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="b3158-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b3158-127">"Containercmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="b3158-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b3158-128">"Navigationcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="b3158-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b3158-129">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="b3158-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
