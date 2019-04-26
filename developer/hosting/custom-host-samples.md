---
title: 自定义主机示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082917"
---
# <a name="custom-host-samples"></a><span data-ttu-id="382d0-102">自定义主机示例</span><span class="sxs-lookup"><span data-stu-id="382d0-102">Custom Host Samples</span></span>

<span data-ttu-id="382d0-103">本部分包含有关编写自定义主机的示例代码。</span><span class="sxs-lookup"><span data-stu-id="382d0-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="382d0-104">可以使用 Microsoft Visual Studio 创建控制台应用程序，然后将此部分中的主题从代码复制到主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="382d0-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="382d0-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="382d0-105">In This Section</span></span>

 <span data-ttu-id="382d0-106">[Host01 示例](./host01-sample.md)此示例演示如何实现使用基本的自定义主机的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="382d0-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="382d0-107">[Host02 示例](./host02-sample.md)此示例演示如何编写使用 Windows PowerShell 运行时与自定义主机实现的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="382d0-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="382d0-108">主机应用程序将主机区域性设置为 German，运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，并显示将结果作为你会看到它们在德语中使用 pwrsh.exe，然后打印出当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="382d0-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="382d0-109">[Host03 示例](./host03-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="382d0-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="382d0-110">[Host04 示例](./host04-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="382d0-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="382d0-111">此主机应用程序还支持显示允许用户指定多个选项的提示。</span><span class="sxs-lookup"><span data-stu-id="382d0-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="382d0-112">[Host05 示例](./host05-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="382d0-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="382d0-113">此主机应用程序还支持对远程计算机的调用使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)并[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet</span><span class="sxs-lookup"><span data-stu-id="382d0-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="382d0-114">[Host06 示例](./host06-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="382d0-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="382d0-115">此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。</span><span class="sxs-lookup"><span data-stu-id="382d0-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="382d0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="382d0-116">See Also</span></span>
