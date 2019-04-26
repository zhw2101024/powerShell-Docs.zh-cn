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
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081285"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="bf491-102">RunSpace07 代码示例</span><span class="sxs-lookup"><span data-stu-id="bf491-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="bf491-103">此处是 Runspace07 示例中所述的源代码[创建控制台应用程序，将添加命令到管道](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)。</span><span class="sxs-lookup"><span data-stu-id="bf491-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="bf491-104">此示例应用程序创建一个运行空间、 创建管道，将两个命令添加到管道中，然后执行管道。</span><span class="sxs-lookup"><span data-stu-id="bf491-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="bf491-105">添加到管道的命令是`Get-Process`和`Measure-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf491-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="bf491-106">您可以下载C#源文件 (runspace07.cs) 使用的 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件。</span><span class="sxs-lookup"><span data-stu-id="bf491-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bf491-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="bf491-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bf491-108">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="bf491-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bf491-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="bf491-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="bf491-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf491-110">See Also</span></span>

[<span data-ttu-id="bf491-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="bf491-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bf491-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bf491-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)