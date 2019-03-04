---
title: GetProc04 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 02b692047294879f885ca86d4598b0b0ab81808a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863283"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="de0bc-102">GetProc04 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="de0bc-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="de0bc-103">下面的代码演示如何实现`Get-Process`cmdlet，它报告非终止错误。</span><span class="sxs-lookup"><span data-stu-id="de0bc-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="de0bc-104">此实现会调用[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)报告非终止错误的方法。</span><span class="sxs-lookup"><span data-stu-id="de0bc-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="de0bc-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="de0bc-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="de0bc-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="de0bc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="de0bc-107">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="de0bc-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="de0bc-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="de0bc-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="de0bc-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="de0bc-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="de0bc-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="de0bc-110">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="de0bc-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de0bc-111">See Also</span></span>

[<span data-ttu-id="de0bc-112">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="de0bc-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="de0bc-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="de0bc-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)