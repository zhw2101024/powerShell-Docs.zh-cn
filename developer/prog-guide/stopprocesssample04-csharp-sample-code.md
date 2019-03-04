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
ms.openlocfilehash: 5a9e7a9ea13c9a62440b7cd80285751c901bcdd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862713"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="2b49b-102">StopProcessSample04 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="2b49b-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="2b49b-103">下面是完整C#StopProc04 示例 cmdlet 的示例代码。</span><span class="sxs-lookup"><span data-stu-id="2b49b-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="2b49b-104">这是代码`Stop-Process`中所述的 cmdlet[添加到 Cmdlet 的参数集](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="2b49b-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="2b49b-105">`Stop-Process` Cmdlet 旨在用于停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="2b49b-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="2b49b-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此停止进程 cmdlet (stopprocesssample04.cs) 源文件。</span><span class="sxs-lookup"><span data-stu-id="2b49b-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b49b-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="2b49b-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2b49b-108">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此停止进程 cmdlet (stopprocesssample04.cs) 源文件。</span><span class="sxs-lookup"><span data-stu-id="2b49b-108">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b49b-109">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="2b49b-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2b49b-110">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="2b49b-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="2b49b-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b49b-111">See Also</span></span>

[<span data-ttu-id="2b49b-112">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="2b49b-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2b49b-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b49b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)