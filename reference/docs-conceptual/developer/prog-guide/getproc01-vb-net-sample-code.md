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
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360436"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="8f24d-102">GetProc01 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="8f24d-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="8f24d-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="8f24d-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="8f24d-104">请注意，通过将进程检索的实际工作保留给[Getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法，可简化 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8f24d-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="8f24d-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getproc01.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="8f24d-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8f24d-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="8f24d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8f24d-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="8f24d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8f24d-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="8f24d-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="8f24d-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f24d-109">See Also</span></span>

[<span data-ttu-id="8f24d-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="8f24d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8f24d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8f24d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)