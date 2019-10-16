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
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360126"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="b9f67-102">RunSpace09 代码示例</span><span class="sxs-lookup"><span data-stu-id="b9f67-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="b9f67-103">下面是[创建一个以异步方式调用管道的控制台应用程序](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)中所述的 Runspace09 示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="b9f67-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="b9f67-104">此示例应用程序创建并打开运行空间，创建并异步调用管道，然后使用管道事件异步处理脚本。</span><span class="sxs-lookup"><span data-stu-id="b9f67-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="b9f67-105">此应用程序运行的脚本将以0.5 秒为间隔创建整数1到10（500毫秒）。</span><span class="sxs-lookup"><span data-stu-id="b9f67-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="b9f67-106">代码示例</span><span class="sxs-lookup"><span data-stu-id="b9f67-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="b9f67-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9f67-107">See Also</span></span>

[<span data-ttu-id="b9f67-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b9f67-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
