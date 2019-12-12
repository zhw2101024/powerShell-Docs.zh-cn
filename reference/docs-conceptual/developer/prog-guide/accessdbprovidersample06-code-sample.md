---
title: AccessDbProviderSample06 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 7f75a3a3d2ab89696bb34ec2fdf7ba7a5ce0f9b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416238"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="f0ca1-102">AccessDbProviderSample06 代码示例</span><span class="sxs-lookup"><span data-stu-id="f0ca1-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="f0ca1-103">下面的代码演示了在[创建 Windows Powershell 内容提供程序](./creating-a-windows-powershell-content-provider.md)中介绍的 windows powershell 内容提供程序的实现。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="f0ca1-104">此提供程序使用户能够操作数据存储区中的项的内容。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="f0ca1-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此访问接口的源文件（AccessDBSampleProvider06.cs）。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f0ca1-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f0ca1-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="f0ca1-108">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ca1-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="f0ca1-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="f0ca1-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="f0ca1-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0ca1-110">See Also</span></span>

[<span data-ttu-id="f0ca1-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="f0ca1-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f0ca1-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f0ca1-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
