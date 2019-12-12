---
title: StopProcessSample04 （C#）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: df5591e351790d18bf2a5b5554d792ab8175dcc6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416041"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="2f346-102">StopProcessSample04 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="2f346-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="2f346-103">下面是 StopProc04 cmdlet C#的完整示例代码。</span><span class="sxs-lookup"><span data-stu-id="2f346-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="2f346-104">这是[将参数集添加到 cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述的 `Stop-Process` cmdlet 的代码。</span><span class="sxs-lookup"><span data-stu-id="2f346-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="2f346-105">`Stop-Process` cmdlet 旨在停止使用 Get-help cmdlet （在[创建第一个 cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)中介绍）检索的进程。</span><span class="sxs-lookup"><span data-stu-id="2f346-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="2f346-106">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 stopprocesssample04.cs cmdlet 的（）源文件。</span><span class="sxs-lookup"><span data-stu-id="2f346-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2f346-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="2f346-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2f346-108">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="2f346-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="2f346-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f346-109">See Also</span></span>

[<span data-ttu-id="2f346-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="2f346-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2f346-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2f346-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
