---
title: RunSpace10 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: fcc424f83275452e223ef025cc8d95128520bdbc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417867"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="69513-102">RunSpace10 代码示例</span><span class="sxs-lookup"><span data-stu-id="69513-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="69513-103">下面是 Runspace10 示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="69513-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="69513-104">此示例应用程序将 cmdlet 添加到[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然后使用修改后的配置信息来创建运行空间。</span><span class="sxs-lookup"><span data-stu-id="69513-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="69513-105">您可以使用适用C#于 windows Vista 的 Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载源文件（runspace10.cs）。</span><span class="sxs-lookup"><span data-stu-id="69513-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="69513-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="69513-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="69513-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="69513-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="69513-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="69513-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="69513-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="69513-109">See Also</span></span>

[<span data-ttu-id="69513-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="69513-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="69513-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="69513-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
