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
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734972"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="56b11-102">RunSpace05 代码示例</span><span class="sxs-lookup"><span data-stu-id="56b11-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="56b11-103">以下是中所述的 Runspace05 示例源代码[配置的运行空间使用 RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)。</span><span class="sxs-lookup"><span data-stu-id="56b11-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="56b11-104">此示例演示如何创建运行空间配置信息、 创建的运行空间，使用单个命令，创建一个管道并执行管道。</span><span class="sxs-lookup"><span data-stu-id="56b11-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="56b11-105">执行的命令是`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56b11-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="56b11-106">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的源文件 (runspace05.cs)。</span><span class="sxs-lookup"><span data-stu-id="56b11-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="56b11-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="56b11-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="56b11-108">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="56b11-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="56b11-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="56b11-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="56b11-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56b11-110">See Also</span></span>

[<span data-ttu-id="56b11-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="56b11-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="56b11-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="56b11-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)