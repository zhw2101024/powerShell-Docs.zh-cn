---
title: RunSpace04 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: e9a79e90da7e0a8232280fa2275d357cb633f4d6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416072"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="c0c1a-102">RunSpace04 代码示例</span><span class="sxs-lookup"><span data-stu-id="c0c1a-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="c0c1a-103">下面是使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来执行生成终止错误的脚本的运行空间的代码示例。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="c0c1a-104">宿主应用程序负责捕获错误并解释错误记录。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="c0c1a-105">你可以使用适用于 Windows Vista 的 Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此运行空间的 VB.NET 源文件（Runspace04）。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c0c1a-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c0c1a-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c0c1a-108">有关完整的示例代码，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="c0c1a-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c0c1a-109">Language</span><span class="sxs-lookup"><span data-stu-id="c0c1a-109">Language</span></span>|<span data-ttu-id="c0c1a-110">主题</span><span class="sxs-lookup"><span data-stu-id="c0c1a-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c0c1a-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c0c1a-111">VB.NET</span></span>|[<span data-ttu-id="c0c1a-112">Runspace01 （VB.NET）代码示例</span><span class="sxs-lookup"><span data-stu-id="c0c1a-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="c0c1a-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0c1a-113">See Also</span></span>

[<span data-ttu-id="c0c1a-114">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="c0c1a-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c0c1a-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c0c1a-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
