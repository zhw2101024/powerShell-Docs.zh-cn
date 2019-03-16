---
title: Cmdlet 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056248"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="6839e-102">Cmdlet 代码示例</span><span class="sxs-lookup"><span data-stu-id="6839e-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="6839e-103">本部分包含可用于开始编写自己的 cmdlet 的 cmdlet 代码的示例。</span><span class="sxs-lookup"><span data-stu-id="6839e-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6839e-104">如果您想编写 cmdlet 的分步说明，请参阅[编写的 Cmdlet 的教程](./tutorials-for-writing-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="6839e-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6839e-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="6839e-105">In This Section</span></span>

<span data-ttu-id="6839e-106">[如何编写简单的 Cmdlet](./how-to-write-a-simple-cmdlet.md)此示例中显示的 cmdlet 代码的基本结构。</span><span class="sxs-lookup"><span data-stu-id="6839e-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="6839e-107">[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)此示例演示如何声明不同类型的参数。</span><span class="sxs-lookup"><span data-stu-id="6839e-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="6839e-108">[如何声明参数集](./how-to-declare-parameter-sets.md)此示例演示如何声明的可更改在 cmdlet 执行的操作的参数集。</span><span class="sxs-lookup"><span data-stu-id="6839e-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="6839e-109">[如何验证参数输入](./how-to-validate-parameter-input.md)这些示例演示如何验证参数输入。</span><span class="sxs-lookup"><span data-stu-id="6839e-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="6839e-110">[如何声明动态参数](./how-to-declare-dynamic-parameters.md)此示例演示如何声明在运行时添加的参数。</span><span class="sxs-lookup"><span data-stu-id="6839e-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="6839e-111">[如何在 Cmdlet 内调用脚本](./how-to-invoke-scripts-within-a-cmdlet.md)此示例演示如何调用脚本提供给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6839e-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="6839e-112">[如何重写输入处理方法](./how-to-override-input-processing-methods.md)这些示例显示用于重写 BeginProcessing、 ProcessRecord 和 EndProcessing 方法的基本结构。</span><span class="sxs-lookup"><span data-stu-id="6839e-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="6839e-113">[如何支持 ShouldProcess 调用](./how-to-request-confirmations.md)此示例演示如何[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)在 cmdlet 内，应从调用的方法。</span><span class="sxs-lookup"><span data-stu-id="6839e-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="6839e-114">[如何支持事务](./how-to-support-transactions.md)此示例演示如何以指示该 cmdlet 支持事务以及如何实现在一个事务内使用此 cmdlet 时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="6839e-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="6839e-115">[如何支持作业](./how-to-support-jobs.md)此示例演示如何编写 cmdlet 时支持的作业。</span><span class="sxs-lookup"><span data-stu-id="6839e-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="6839e-116">[如何调用 Cmdlet 从内 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)此示例演示如何调用在另一个 cmdlet，后者允许您将调用 cmdlet 的功能添加到该 cmdlet 正在开发中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6839e-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="6839e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6839e-117">See Also</span></span>

[<span data-ttu-id="6839e-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6839e-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
