---
title: GetProc01 （VB.NET）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 80f145da8f4e2f3a39b1cdd533478b7fdc2f0a31
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417447"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="50c46-102">GetProc01 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="50c46-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="50c46-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="50c46-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="50c46-104">请注意，通过将进程检索的实际工作保留给[Getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法，可简化 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="50c46-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="50c46-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getproc01.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="50c46-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="50c46-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="50c46-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="50c46-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="50c46-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="50c46-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="50c46-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="50c46-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="50c46-109">See Also</span></span>

[<span data-ttu-id="50c46-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="50c46-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="50c46-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="50c46-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
