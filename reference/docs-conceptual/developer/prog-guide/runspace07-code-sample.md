---
title: RunSpace07 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: f40b24951c44c228d85524845045aea58f680f2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870602"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="ac6d8-102">RunSpace07 代码示例</span><span class="sxs-lookup"><span data-stu-id="ac6d8-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="ac6d8-103">下面是[创建将命令添加到管道的控制台应用程序](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述的 Runspace07 示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="ac6d8-104">此示例应用程序创建运行空间，创建管道，将两个命令添加到管道，然后执行管道。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="ac6d8-105">添加到管道中的命令是 `Get-Process` 和 `Measure-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6d8-106">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载源文件（runspace07.cs）。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ac6d8-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ac6d8-108">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ac6d8-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="ac6d8-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="ac6d8-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac6d8-110">See Also</span></span>

[<span data-ttu-id="ac6d8-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="ac6d8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ac6d8-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ac6d8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
