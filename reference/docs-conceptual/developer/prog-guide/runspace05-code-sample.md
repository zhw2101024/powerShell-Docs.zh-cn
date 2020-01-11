---
title: RunSpace05 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 8802e308712be93992ead5ef77b97d8c21b137f7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870636"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="fd03e-102">RunSpace05 代码示例</span><span class="sxs-lookup"><span data-stu-id="fd03e-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="fd03e-103">下面是[使用 RunspaceConfiguration 配置运行空间](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述的 Runspace05 示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="fd03e-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="fd03e-104">此示例演示如何创建运行空间配置信息、创建运行空间、使用单个命令创建管道，然后执行管道。</span><span class="sxs-lookup"><span data-stu-id="fd03e-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="fd03e-105">执行的命令是 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd03e-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="fd03e-106">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载源文件（runspace05.cs）。</span><span class="sxs-lookup"><span data-stu-id="fd03e-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fd03e-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="fd03e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="fd03e-108">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="fd03e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fd03e-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="fd03e-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="fd03e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd03e-110">See Also</span></span>

[<span data-ttu-id="fd03e-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="fd03e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fd03e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fd03e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
