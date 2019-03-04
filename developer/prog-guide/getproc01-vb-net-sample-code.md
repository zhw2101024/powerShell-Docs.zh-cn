---
title: GetProc01 (VB.NET) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856063"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="d319d-102">GetProc01 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="d319d-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="d319d-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="d319d-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="d319d-104">请注意，该 cmdlet 简化了离开进程检索到的实际工作[System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法。</span><span class="sxs-lookup"><span data-stu-id="d319d-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="d319d-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="d319d-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d319d-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="d319d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d319d-107">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="d319d-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d319d-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="d319d-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d319d-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="d319d-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d319d-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="d319d-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="d319d-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d319d-111">See Also</span></span>

[<span data-ttu-id="d319d-112">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="d319d-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d319d-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d319d-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)