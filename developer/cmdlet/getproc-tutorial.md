---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862453"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="7ce28-102">GetProc 教程</span><span class="sxs-lookup"><span data-stu-id="7ce28-102">GetProc Tutorial</span></span>

<span data-ttu-id="7ce28-103">本部分提供的教程，创建一个 Get-proc cmdlet 是非常类似于[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)提供的 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ce28-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="7ce28-104">本教程提供的演示了如何实现 cmdlet 的代码片段和代码的说明。</span><span class="sxs-lookup"><span data-stu-id="7ce28-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="7ce28-105">在本教程中的主题</span><span class="sxs-lookup"><span data-stu-id="7ce28-105">Topics in this Tutorial</span></span>

<span data-ttu-id="7ce28-106">在本教程中的主题旨在使用在上一主题中讨论的内容构建每个主题按顺序读取。</span><span class="sxs-lookup"><span data-stu-id="7ce28-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="7ce28-107">[创建不带参数的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本部分介绍如何创建从本地计算机而不使用参数，检索的信息，然后将信息写入管道的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ce28-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="7ce28-108">[将该进程命令行输入参数添加](./adding-parameters-that-process-command-line-input.md)本部分介绍如何将参数添加到 Get-proc cmdlet，以便该 cmdlet 可以处理基于显式对象传递给 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="7ce28-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="7ce28-109">中介绍的实现此处检索的过程基于其名称，，然后将信息写入管道。</span><span class="sxs-lookup"><span data-stu-id="7ce28-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="7ce28-110">[添加参数该进程管道输入](./adding-parameters-that-process-pipeline-input.md)本部分介绍如何将参数添加到 Get-proc cmdlet，以便该 cmdlet 可以处理通过管道传递给它的对象。</span><span class="sxs-lookup"><span data-stu-id="7ce28-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="7ce28-111">所述实现 cmdlet 此处检索进程基于对象传递给 cmdlet，然后将信息写入到管道。</span><span class="sxs-lookup"><span data-stu-id="7ce28-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="7ce28-112">[将非终止错误报告添加到你的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本部分介绍如何添加非终止错误报告给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ce28-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="7ce28-113">此处所述的实现会检测发生时处理输入，并将错误记录写入错误流的非终止错误。</span><span class="sxs-lookup"><span data-stu-id="7ce28-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce28-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ce28-114">See Also</span></span>

[<span data-ttu-id="7ce28-115">创建不带参数的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce28-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="7ce28-116">添加处理命令行输入的参数</span><span class="sxs-lookup"><span data-stu-id="7ce28-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="7ce28-117">添加进程管道输入的参数</span><span class="sxs-lookup"><span data-stu-id="7ce28-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="7ce28-118">添加非终止错误报告到 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce28-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="7ce28-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7ce28-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
