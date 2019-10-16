---
title: GetProc03 （C#）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 10c41ffd03e9adae82813bfe79d3e15030087953
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360336"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="9911e-102">GetProc03 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="9911e-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="9911e-103">下面的代码演示了可接受管道输入的 `Get-Process` cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="9911e-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="9911e-104">此实现定义了一个 `Name` 参数，该参数接受管道输入，基于提供的名称从本地计算机检索进程信息，然后使用[WriteObject （system.string，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法作为输出用于将对象发送到管道的机制。</span><span class="sxs-lookup"><span data-stu-id="9911e-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="9911e-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此 getprov03.cs cmdlet 的源文件（）。</span><span class="sxs-lookup"><span data-stu-id="9911e-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9911e-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="9911e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9911e-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="9911e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9911e-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="9911e-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="9911e-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9911e-109">See Also</span></span>

[<span data-ttu-id="9911e-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="9911e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9911e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9911e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
