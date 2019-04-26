---
title: GetProc03 (C#) 的示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081506"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="aada6-102">GetProc03 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="aada6-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="aada6-103">下面的代码演示如何实现`Get-Process`cmdlet，它可以接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="aada6-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="aada6-104">此实现中定义`Name`接受管道输入的参数从基于提供的名称，在本地计算机检索进程信息，然后使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为将对象发送到管道的输出机制的方法。</span><span class="sxs-lookup"><span data-stu-id="aada6-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="aada6-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="aada6-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="aada6-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="aada6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="aada6-107">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="aada6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="aada6-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="aada6-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="aada6-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aada6-109">See Also</span></span>

[<span data-ttu-id="aada6-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="aada6-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="aada6-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="aada6-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)