---
title: Windows PowerShell02 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861063"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="50723-102">Windows PowerShell02 示例</span><span class="sxs-lookup"><span data-stu-id="50723-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="50723-103">此示例演示如何使用运行空间的运行空间池以异步方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="50723-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="50723-104">此示例将生成一系列命令，然后运行这些命令，而 Windows PowerShell 引擎将在需要时从池中打开运行空间。</span><span class="sxs-lookup"><span data-stu-id="50723-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="50723-105">要求</span><span class="sxs-lookup"><span data-stu-id="50723-105">Requirements</span></span>

- <span data-ttu-id="50723-106">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="50723-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="50723-107">说明</span><span class="sxs-lookup"><span data-stu-id="50723-107">Demonstrates</span></span>

<span data-ttu-id="50723-108">此示例将演示如下：</span><span class="sxs-lookup"><span data-stu-id="50723-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="50723-109">创建具有最小和最大的可在同一时间打开运行空间数 RunspacePool 对象。</span><span class="sxs-lookup"><span data-stu-id="50723-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="50723-110">创建命令的列表。</span><span class="sxs-lookup"><span data-stu-id="50723-110">Creating a list of commands.</span></span>

- <span data-ttu-id="50723-111">以异步方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="50723-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="50723-112">调用[System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)方法，以便查看多少运行空间是免费的。</span><span class="sxs-lookup"><span data-stu-id="50723-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="50723-113">捕获命令输出中的与[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="50723-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="50723-114">示例</span><span class="sxs-lookup"><span data-stu-id="50723-114">Example</span></span>

<span data-ttu-id="50723-115">此示例演示如何打开运行空间的运行空间池，以及如何以异步方式在这些运行空间中运行命令。</span><span class="sxs-lookup"><span data-stu-id="50723-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="50723-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50723-116">See Also</span></span>

[<span data-ttu-id="50723-117">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="50723-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)