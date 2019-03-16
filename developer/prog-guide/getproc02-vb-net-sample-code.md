---
title: GetProc02 (VB.NET) 的示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056271"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="eaf95-102">GetProc02 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="eaf95-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="eaf95-103">下面的代码演示如何实现`Get-Process`接受命令行输入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eaf95-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="eaf95-104">请注意，此实现中定义`Name`参数，以允许命令行输入，并使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为输出的方法机制，用于将输出发送到管道对象。</span><span class="sxs-lookup"><span data-stu-id="eaf95-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eaf95-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="eaf95-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="eaf95-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eaf95-106">See Also</span></span>

[<span data-ttu-id="eaf95-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="eaf95-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)