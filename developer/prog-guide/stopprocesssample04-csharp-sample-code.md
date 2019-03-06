---
title: StopProcessSample04 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: a09efae487dd34238289a6c13dd7786020f15c7d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429493"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="94dc7-102">StopProcessSample04 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="94dc7-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="94dc7-103">下面是完整C#StopProc04 示例 cmdlet 的示例代码。</span><span class="sxs-lookup"><span data-stu-id="94dc7-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="94dc7-104">这是代码`Stop-Process`中所述的 cmdlet[添加到 Cmdlet 的参数集](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="94dc7-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="94dc7-105">`Stop-Process` Cmdlet 旨在用于停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="94dc7-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="94dc7-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此停止进程 cmdlet (stopprocesssample04.cs) 源文件。</span><span class="sxs-lookup"><span data-stu-id="94dc7-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="94dc7-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="94dc7-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="94dc7-108">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="94dc7-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="94dc7-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94dc7-109">See Also</span></span>

[<span data-ttu-id="94dc7-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="94dc7-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="94dc7-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="94dc7-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)