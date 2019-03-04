---
title: GetProc04 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855443"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="309e7-102">GetProc04 代码示例</span><span class="sxs-lookup"><span data-stu-id="309e7-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="309e7-103">以下是 GetProc04 示例 cmdlet 的代码示例。</span><span class="sxs-lookup"><span data-stu-id="309e7-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="309e7-104">这是`Get-Process`cmdlet 示例中所述[添加非终止错误报告给您 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="309e7-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="309e7-105">这`Get-Process`cmdlet 可调用[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法只要检索进程信息时将引发无效操作异常。</span><span class="sxs-lookup"><span data-stu-id="309e7-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="309e7-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="309e7-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="309e7-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="309e7-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="309e7-108">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="309e7-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="309e7-109">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="309e7-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="309e7-110">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="309e7-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="309e7-111">有关完整的示例代码，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="309e7-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="309e7-112">语言</span><span class="sxs-lookup"><span data-stu-id="309e7-112">Language</span></span>|<span data-ttu-id="309e7-113">主题</span><span class="sxs-lookup"><span data-stu-id="309e7-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="309e7-114">C#</span><span class="sxs-lookup"><span data-stu-id="309e7-114">C#</span></span>|[<span data-ttu-id="309e7-115">GetProc04 (C#) Sample Code</span><span class="sxs-lookup"><span data-stu-id="309e7-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="309e7-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="309e7-116">VB.NET</span></span>|[<span data-ttu-id="309e7-117">GetProc04 (VB.NET) Sample Code</span><span class="sxs-lookup"><span data-stu-id="309e7-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="309e7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="309e7-118">See Also</span></span>

[<span data-ttu-id="309e7-119">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="309e7-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="309e7-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="309e7-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)