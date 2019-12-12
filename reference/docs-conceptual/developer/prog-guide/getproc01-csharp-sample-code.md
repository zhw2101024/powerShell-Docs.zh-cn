---
title: GetProc01 （C#）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416170"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="8f956-102">GetProc01 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="8f956-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="8f956-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="8f956-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="8f956-104">请注意，通过将进程检索的实际工作保留给[Getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法，可简化 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8f956-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="8f956-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getproc01.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="8f956-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8f956-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="8f956-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8f956-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="8f956-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8f956-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="8f956-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="8f956-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f956-109">See Also</span></span>

[<span data-ttu-id="8f956-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="8f956-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8f956-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8f956-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
