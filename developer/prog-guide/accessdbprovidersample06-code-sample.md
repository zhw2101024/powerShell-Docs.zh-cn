---
title: AccessDbProviderSample06 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 2798e8b542b2f06247955409118e75c5652b644c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860783"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="0b902-102">AccessDbProviderSample06 代码示例</span><span class="sxs-lookup"><span data-stu-id="0b902-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="0b902-103">下面的代码演示中所述内容提供商的 Windows powershell 实现[创建一个 Windows PowerShell 内容提供程序](./creating-a-windows-powershell-content-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0b902-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="0b902-104">此提供程序使用户用来处理数据存储区中项的内容。</span><span class="sxs-lookup"><span data-stu-id="0b902-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="0b902-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此提供程序的源文件 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="0b902-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0b902-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0b902-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0b902-107">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此提供程序的源文件 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="0b902-107">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0b902-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0b902-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0b902-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="0b902-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="0b902-110">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0b902-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="0b902-111">代码示例</span><span class="sxs-lookup"><span data-stu-id="0b902-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="0b902-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b902-112">See Also</span></span>

[<span data-ttu-id="0b902-113">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="0b902-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0b902-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b902-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)