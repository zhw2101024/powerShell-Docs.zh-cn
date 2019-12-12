---
title: GetProc04 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417454"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="f24be-102">GetProc04 代码示例</span><span class="sxs-lookup"><span data-stu-id="f24be-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="f24be-103">下面是 GetProc04 cmdlet 的代码示例。</span><span class="sxs-lookup"><span data-stu-id="f24be-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="f24be-104">这是[将非终止错误报告添加到 cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` cmdlet 示例。</span><span class="sxs-lookup"><span data-stu-id="f24be-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="f24be-105">当检索进程信息时引发无效操作异常时，此 `Get-Process` cmdlet 将调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="f24be-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="f24be-106">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getprov04.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="f24be-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f24be-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="f24be-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f24be-108">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="f24be-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="f24be-109">有关完整的示例代码，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="f24be-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="f24be-110">Language</span><span class="sxs-lookup"><span data-stu-id="f24be-110">Language</span></span>|<span data-ttu-id="f24be-111">主题</span><span class="sxs-lookup"><span data-stu-id="f24be-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="f24be-112">C#</span><span class="sxs-lookup"><span data-stu-id="f24be-112">C#</span></span>|[<span data-ttu-id="f24be-113">GetProc04 （C#）示例代码</span><span class="sxs-lookup"><span data-stu-id="f24be-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="f24be-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="f24be-114">VB.NET</span></span>|[<span data-ttu-id="f24be-115">GetProc04 （VB.NET）示例代码</span><span class="sxs-lookup"><span data-stu-id="f24be-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="f24be-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f24be-116">See Also</span></span>

[<span data-ttu-id="f24be-117">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="f24be-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f24be-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f24be-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
