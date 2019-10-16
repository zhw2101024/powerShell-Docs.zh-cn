---
title: GetProc02 （C#）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360366"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="6ef20-102">GetProc02 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="6ef20-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="6ef20-103">下面的代码演示如何实现 `Get-Process` cmdlet，该 cmdlet 接受命令行输入。</span><span class="sxs-lookup"><span data-stu-id="6ef20-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="6ef20-104">请注意，此实现定义了一个允许命令行输入的 `Name` 参数，并使用[WriteObject （system.string，system.object）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法作为将输出对象发送到管道的输出机制。</span><span class="sxs-lookup"><span data-stu-id="6ef20-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6ef20-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="6ef20-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="6ef20-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ef20-106">See Also</span></span>

[<span data-ttu-id="6ef20-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6ef20-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
