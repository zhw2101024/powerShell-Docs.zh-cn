---
title: AccessDbProviderSample02 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416244"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="979cc-102">AccessDbProviderSample02 代码示例</span><span class="sxs-lookup"><span data-stu-id="979cc-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="979cc-103">下面的代码演示了在[创建 Windows Powershell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)中所述的 windows powershell 提供程序的实现。</span><span class="sxs-lookup"><span data-stu-id="979cc-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="979cc-104">此实现创建一个路径，与 Access 数据库建立连接，然后删除该驱动器。</span><span class="sxs-lookup"><span data-stu-id="979cc-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="979cc-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider02.cs）。</span><span class="sxs-lookup"><span data-stu-id="979cc-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="979cc-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="979cc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="979cc-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="979cc-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="979cc-108">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="979cc-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="979cc-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="979cc-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="979cc-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="979cc-110">See Also</span></span>

[<span data-ttu-id="979cc-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="979cc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="979cc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="979cc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
