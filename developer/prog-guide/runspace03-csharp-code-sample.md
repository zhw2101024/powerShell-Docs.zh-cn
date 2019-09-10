---
title: RunSpace03 （C#）代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848028"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="e50e5-102">RunSpace03 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="e50e5-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="e50e5-103">下面是 " C#创建运行指定脚本的控制台应用程序" 中所述的控制台应用程序的源代码。</span><span class="sxs-lookup"><span data-stu-id="e50e5-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="e50e5-104">此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来执行一个脚本，该脚本通过使用传递到脚本的进程名称列表来检索进程信息。</span><span class="sxs-lookup"><span data-stu-id="e50e5-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="e50e5-105">它演示如何将输入对象传递给脚本，以及如何检索错误对象以及输出对象。</span><span class="sxs-lookup"><span data-stu-id="e50e5-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="e50e5-106">你可以使用适用C#于 Windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此示例的源文件（runspace03.cs）。</span><span class="sxs-lookup"><span data-stu-id="e50e5-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e50e5-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e50e5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e50e5-108">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="e50e5-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e50e5-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="e50e5-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="e50e5-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e50e5-110">See Also</span></span>

[<span data-ttu-id="e50e5-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="e50e5-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e50e5-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e50e5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)