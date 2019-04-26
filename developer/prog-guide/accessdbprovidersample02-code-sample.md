---
title: AccessDbProviderSample02 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082017"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="3a97c-102">AccessDbProviderSample02 代码示例</span><span class="sxs-lookup"><span data-stu-id="3a97c-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="3a97c-103">下面的代码演示中所述的 Windows PowerShell 提供程序实现[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3a97c-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="3a97c-104">此实现创建一个路径，使用连接到 Access 数据库，然后删除驱动器。</span><span class="sxs-lookup"><span data-stu-id="3a97c-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="3a97c-105">您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider02.cs)。</span><span class="sxs-lookup"><span data-stu-id="3a97c-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3a97c-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="3a97c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3a97c-107">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="3a97c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="3a97c-108">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3a97c-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="3a97c-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="3a97c-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="3a97c-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a97c-110">See Also</span></span>

[<span data-ttu-id="3a97c-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="3a97c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3a97c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3a97c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)