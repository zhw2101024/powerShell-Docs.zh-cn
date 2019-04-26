---
title: AccessDbProviderSample01 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081982"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="429e1-102">AccessDbProviderSample01 代码示例</span><span class="sxs-lookup"><span data-stu-id="429e1-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="429e1-103">下面的代码演示中所述的 Windows PowerShell 提供程序实现[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="429e1-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="429e1-104">此实现提供用于启动和停止提供程序，方法，虽然它不提供一种方法来访问数据存储区或要获取或设置数据存储区中的数据，但它提供所需的所有提供程序的基本功能。</span><span class="sxs-lookup"><span data-stu-id="429e1-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="429e1-105">您可以下载C#的 Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider01.cs)。</span><span class="sxs-lookup"><span data-stu-id="429e1-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="429e1-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="429e1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="429e1-107">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="429e1-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="429e1-108">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="429e1-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="429e1-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="429e1-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="429e1-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="429e1-110">See Also</span></span>

[<span data-ttu-id="429e1-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="429e1-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="429e1-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="429e1-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)