---
title: 非终止错误 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067648"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="9eb15-102">非终止错误</span><span class="sxs-lookup"><span data-stu-id="9eb15-102">Non-Terminating Errors</span></span>

<span data-ttu-id="9eb15-103">本主题讨论用于报告非终止性错误的方法。</span><span class="sxs-lookup"><span data-stu-id="9eb15-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="9eb15-104">它还讨论了如何调用从 cmdlet 中的方法。</span><span class="sxs-lookup"><span data-stu-id="9eb15-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="9eb15-105">发生非终止错误时，该 cmdlet 应通过调用报告此错误[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="9eb15-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="9eb15-106">当该 cmdlet 报告一个非终止错误时，该 cmdlet 可以继续运行由此输入对象和更多传入管道对象。</span><span class="sxs-lookup"><span data-stu-id="9eb15-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="9eb15-107">如果该 cmdlet 调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，该 cmdlet 可以编写错误记录描述导致非终止错误条件。</span><span class="sxs-lookup"><span data-stu-id="9eb15-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="9eb15-108">错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="9eb15-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="9eb15-109">Cmdlet 可以调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)在必要时从其输入处理方法中。</span><span class="sxs-lookup"><span data-stu-id="9eb15-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="9eb15-110">但是，可以调用 cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)只从调用线程[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="9eb15-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="9eb15-111">不要调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)从另一个线程。</span><span class="sxs-lookup"><span data-stu-id="9eb15-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="9eb15-112">相反，通信将错误追溯到主线程。</span><span class="sxs-lookup"><span data-stu-id="9eb15-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eb15-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9eb15-113">See Also</span></span>

[<span data-ttu-id="9eb15-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="9eb15-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="9eb15-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="9eb15-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="9eb15-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="9eb15-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="9eb15-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="9eb15-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="9eb15-118">Windows PowerShell 错误记录</span><span class="sxs-lookup"><span data-stu-id="9eb15-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="9eb15-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9eb15-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
