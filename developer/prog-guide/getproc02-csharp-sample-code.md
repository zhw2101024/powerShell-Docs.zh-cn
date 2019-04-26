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
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081699"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="6f111-102">GetProc02 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="6f111-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="6f111-103">下面的代码演示如何实现`Get-Process`接受命令行输入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f111-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="6f111-104">请注意，此实现中定义`Name`参数，以允许命令行输入，并使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为输出的方法机制，用于将输出发送到管道对象。</span><span class="sxs-lookup"><span data-stu-id="6f111-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6f111-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="6f111-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="6f111-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f111-106">See Also</span></span>

[<span data-ttu-id="6f111-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6f111-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)