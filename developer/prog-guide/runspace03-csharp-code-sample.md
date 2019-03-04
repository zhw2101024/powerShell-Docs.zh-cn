---
title: RunSpace03 (C#) 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: d2e5b8c0a7622481bfca21d5c5b46afa01c02d2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863523"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="03ffd-102">RunSpace03 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="03ffd-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="03ffd-103">下面是C#中所述的控制台应用程序的源代码[创建指定脚本的控制台应用程序，运行](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68)。</span><span class="sxs-lookup"><span data-stu-id="03ffd-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="03ffd-104">此示例使用[System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类，以执行检索使用传递到该脚本的进程名称的列表来处理信息的脚本。</span><span class="sxs-lookup"><span data-stu-id="03ffd-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="03ffd-105">它演示如何将输入的对象传递给脚本以及如何检索错误对象和输出对象。</span><span class="sxs-lookup"><span data-stu-id="03ffd-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="03ffd-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此示例的源文件 (runspace03.cs)。</span><span class="sxs-lookup"><span data-stu-id="03ffd-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="03ffd-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="03ffd-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="03ffd-108">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此示例的源文件 (runspace03.cs)。</span><span class="sxs-lookup"><span data-stu-id="03ffd-108">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="03ffd-109">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="03ffd-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="03ffd-110">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="03ffd-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="03ffd-111">代码示例</span><span class="sxs-lookup"><span data-stu-id="03ffd-111">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="03ffd-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03ffd-112">See Also</span></span>

[<span data-ttu-id="03ffd-113">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="03ffd-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="03ffd-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="03ffd-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)