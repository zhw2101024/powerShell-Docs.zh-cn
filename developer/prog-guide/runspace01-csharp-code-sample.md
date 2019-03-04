---
title: Runspace01 (C#) 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854213"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="42a79-102">Runspace01 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="42a79-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="42a79-103">以下是代码示例的运行空间中所述[创建控制台应用程序，运行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。</span><span class="sxs-lookup"><span data-stu-id="42a79-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="42a79-104">若要执行此操作，该应用程序调用一个运行空间，并调用命令。</span><span class="sxs-lookup"><span data-stu-id="42a79-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="42a79-105">（请注意，此应用程序未指定的运行空间配置信息，也不它不会显式创建的管道。）</span><span class="sxs-lookup"><span data-stu-id="42a79-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="42a79-106">调用的命令是`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42a79-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="42a79-107">以下是代码示例的运行空间中所述[创建控制台应用程序，运行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。</span><span class="sxs-lookup"><span data-stu-id="42a79-107">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="42a79-108">若要执行此操作，该应用程序调用一个运行空间，并调用命令。</span><span class="sxs-lookup"><span data-stu-id="42a79-108">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="42a79-109">（请注意，此应用程序未指定的运行空间配置信息，也不它不会显式创建的管道。）</span><span class="sxs-lookup"><span data-stu-id="42a79-109">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="42a79-110">调用的命令是`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42a79-110">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="42a79-111">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此运行空间的源文件 (runspace01.cs)。</span><span class="sxs-lookup"><span data-stu-id="42a79-111">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="42a79-112">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="42a79-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="42a79-113">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此运行空间的源文件 (runspace01.cs)。</span><span class="sxs-lookup"><span data-stu-id="42a79-113">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="42a79-114">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="42a79-114">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="42a79-115">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="42a79-115">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="42a79-116">代码示例</span><span class="sxs-lookup"><span data-stu-id="42a79-116">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="42a79-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42a79-117">See Also</span></span>

[<span data-ttu-id="42a79-118">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="42a79-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="42a79-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="42a79-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)