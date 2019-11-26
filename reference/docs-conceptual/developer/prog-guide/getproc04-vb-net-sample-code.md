---
title: GetProc04 （VB.NET）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416094"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="17a76-102">GetProc04 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="17a76-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="17a76-103">下面的代码演示了用于报告非终止错误的 `Get-Process` cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="17a76-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="17a76-104">此实现将调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法来报告非终止错误。</span><span class="sxs-lookup"><span data-stu-id="17a76-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="17a76-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getprov04.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="17a76-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="17a76-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="17a76-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="17a76-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="17a76-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="17a76-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="17a76-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="17a76-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="17a76-109">See Also</span></span>

[<span data-ttu-id="17a76-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="17a76-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="17a76-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="17a76-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
