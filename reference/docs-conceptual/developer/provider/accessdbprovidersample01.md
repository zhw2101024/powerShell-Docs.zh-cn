---
title: AccessDBProviderSample01 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359996"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="1d1ac-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="1d1ac-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="1d1ac-103">此示例演示如何声明一个直接从[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类派生的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="1d1ac-104">仅出于完整性考虑而在此处包含此项。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1d1ac-105">示例</span><span class="sxs-lookup"><span data-stu-id="1d1ac-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d1ac-106">提供程序类最有可能派生自以下类之一，并可能实现其他提供程序接口：</span><span class="sxs-lookup"><span data-stu-id="1d1ac-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="1d1ac-107">" [Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="1d1ac-108">请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="1d1ac-109">" [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="1d1ac-110">请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="1d1ac-111">" [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) " 类。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="1d1ac-112">请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="1d1ac-113">有关根据提供程序功能选择要从哪个提供程序类派生的详细信息，请参阅[设计你的 Windows PowerShell 提供程序](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="1d1ac-114">此示例演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="1d1ac-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="1d1ac-115">声明 `CmdletProvider` 属性。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="1d1ac-116">定义直接从[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类中派生的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="1d1ac-117">示例</span><span class="sxs-lookup"><span data-stu-id="1d1ac-117">Example</span></span>

<span data-ttu-id="1d1ac-118">此示例演示如何定义提供程序类以及如何声明 `CmdletProvider` 属性。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="1d1ac-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d1ac-119">See Also</span></span>

[<span data-ttu-id="1d1ac-120">"Itemcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="1d1ac-121">"Containercmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="1d1ac-122">"Navigationcmdletprovider"。</span><span class="sxs-lookup"><span data-stu-id="1d1ac-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="1d1ac-123">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="1d1ac-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)