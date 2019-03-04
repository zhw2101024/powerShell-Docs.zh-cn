---
title: GetProc02 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 740e8d60b71654b82020d16b2964165f3ee1e600
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862303"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="1991f-102">GetProc02 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="1991f-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="1991f-103">下面的代码演示如何实现`Get-Process`接受命令行输入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1991f-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="1991f-104">请注意，此实现中定义`Name`参数，以允许命令行输入，并使用[System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为输出的方法机制，用于将输出发送到管道对象。</span><span class="sxs-lookup"><span data-stu-id="1991f-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1991f-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="1991f-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="1991f-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1991f-106">See Also</span></span>

[<span data-ttu-id="1991f-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1991f-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)