---
title: GetProc03 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857303"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="6d022-102">GetProc03 代码示例</span><span class="sxs-lookup"><span data-stu-id="6d022-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="6d022-103">以下是 GetProc03 示例 cmdlet 的代码示例。</span><span class="sxs-lookup"><span data-stu-id="6d022-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="6d022-104">这是`Get-Process`cmdlet 示例中所述[添加该进程管道输入的参数](../cmdlet/adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6d022-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="6d022-105">这`Get-Process`cmdlet 使用`Name`接受来自管道对象的输入参数从基于提供的名称，在本地计算机检索进程信息，然后在命令行中显示有关进程的信息。</span><span class="sxs-lookup"><span data-stu-id="6d022-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="6d022-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="6d022-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6d022-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="6d022-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6d022-108">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="6d022-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6d022-109">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="6d022-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6d022-110">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="6d022-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="6d022-111">有关完整的示例代码，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="6d022-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="6d022-112">语言</span><span class="sxs-lookup"><span data-stu-id="6d022-112">Language</span></span>|<span data-ttu-id="6d022-113">主题</span><span class="sxs-lookup"><span data-stu-id="6d022-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="6d022-114">C#</span><span class="sxs-lookup"><span data-stu-id="6d022-114">C#</span></span>|[<span data-ttu-id="6d022-115">GetProc03 (C#) 的示例代码</span><span class="sxs-lookup"><span data-stu-id="6d022-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="6d022-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="6d022-116">VB.NET</span></span>|[<span data-ttu-id="6d022-117">GetProc03 (VB.NET) 的示例代码</span><span class="sxs-lookup"><span data-stu-id="6d022-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="6d022-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d022-118">See Also</span></span>

[<span data-ttu-id="6d022-119">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="6d022-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6d022-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6d022-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)