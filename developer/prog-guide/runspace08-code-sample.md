---
title: RunSpace08 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081268"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="b824b-102">RunSpace08 代码示例</span><span class="sxs-lookup"><span data-stu-id="b824b-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="b824b-103">此处是 Runspace08 示例中所述的源代码[创建控制台应用程序，将添加命令参数](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)。</span><span class="sxs-lookup"><span data-stu-id="b824b-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="b824b-104">此示例应用程序创建一个运行空间、 创建管道，将两个命令添加到管道，将两个参数添加到第二个命令，然后执行管道。</span><span class="sxs-lookup"><span data-stu-id="b824b-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="b824b-105">添加到管道的命令是`Get-Process`和`Sort-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b824b-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b824b-106">代码示例</span><span class="sxs-lookup"><span data-stu-id="b824b-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="b824b-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b824b-107">See Also</span></span>

[<span data-ttu-id="b824b-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b824b-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)