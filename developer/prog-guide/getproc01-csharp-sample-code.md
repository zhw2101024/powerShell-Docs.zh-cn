---
title: GetProc01 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 56ce7080e24cc12de6d43ac607ffd5d3f0a3b17c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856883"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="ae4ef-102">GetProc01 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="ae4ef-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="ae4ef-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="ae4ef-104">请注意，该 cmdlet 简化了离开进程检索到的实际工作[System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="ae4ef-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ae4ef-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ae4ef-107">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ae4ef-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ae4ef-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="ae4ef-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ae4ef-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="ae4ef-110">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="ae4ef-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae4ef-111">See Also</span></span>

[<span data-ttu-id="ae4ef-112">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="ae4ef-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ae4ef-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ae4ef-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)