---
title: StopProc 教程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067292"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="77f4b-102">StopProc 教程</span><span class="sxs-lookup"><span data-stu-id="77f4b-102">StopProc Tutorial</span></span>

<span data-ttu-id="77f4b-103">本部分提供有关创建停止进程 cmdlet，它是非常相似的教程[Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)提供的 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77f4b-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="77f4b-104">本教程提供的演示了如何实现 cmdlet 的代码片段和代码的说明。</span><span class="sxs-lookup"><span data-stu-id="77f4b-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="77f4b-105">在本教程中的主题</span><span class="sxs-lookup"><span data-stu-id="77f4b-105">Topics in this Tutorial</span></span>

<span data-ttu-id="77f4b-106">在本教程中的主题旨在使用在上一主题中讨论的内容构建每个主题按顺序读取。</span><span class="sxs-lookup"><span data-stu-id="77f4b-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="77f4b-107">[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)本部分介绍如何创建支持系统修改，例如停止的计算机上运行的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77f4b-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="77f4b-108">[将用户消息添加到你的 Cmdlet](./adding-user-messages-to-your-cmdlet.md)本部分介绍如何将添加到 cmdlet 中写入用户消息、 调试消息、 警告消息和进度信息的能力。</span><span class="sxs-lookup"><span data-stu-id="77f4b-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="77f4b-109">[添加别名，通配符扩展，并帮助对 Cmdlet 参数](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)本部分介绍如何创建支持参数的别名、 帮助和通配符扩展的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77f4b-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="77f4b-110">[添加到 Cmdlet 的参数可设置](./adding-parameter-sets-to-a-cmdlet.md)本部分介绍如何将添加到 cmdlet 的参数集。</span><span class="sxs-lookup"><span data-stu-id="77f4b-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="77f4b-111">参数集允许运行该 cmdlet 以不同的方式根据用户指定哪些参数。</span><span class="sxs-lookup"><span data-stu-id="77f4b-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="77f4b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77f4b-112">See Also</span></span>

[<span data-ttu-id="77f4b-113">创建一个 Cmdlet 来修改系统</span><span class="sxs-lookup"><span data-stu-id="77f4b-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="77f4b-114">将用户消息添加到你的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77f4b-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="77f4b-115">添加别名，通配符扩展，并帮助对 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="77f4b-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="77f4b-116">向 Cmdlet 添加参数集</span><span class="sxs-lookup"><span data-stu-id="77f4b-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="77f4b-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="77f4b-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
