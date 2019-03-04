---
title: RunSpace09 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854043"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="4be97-102">RunSpace09 代码示例</span><span class="sxs-lookup"><span data-stu-id="4be97-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="4be97-103">此处是 Runspace09 示例中所述的源代码[管道以异步方式创建控制台应用程序，会调用](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)。</span><span class="sxs-lookup"><span data-stu-id="4be97-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="4be97-104">此示例应用程序创建和打开运行空间中，创建并以异步方式调用管道，并使用然后管道事件来以异步方式处理该脚本。</span><span class="sxs-lookup"><span data-stu-id="4be97-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="4be97-105">运行此应用程序的脚本在 0.5 秒时间间隔内 （500 毫秒） 中创建整数 1 到 10。</span><span class="sxs-lookup"><span data-stu-id="4be97-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="4be97-106">代码示例</span><span class="sxs-lookup"><span data-stu-id="4be97-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="4be97-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4be97-107">See Also</span></span>

[<span data-ttu-id="4be97-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4be97-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)