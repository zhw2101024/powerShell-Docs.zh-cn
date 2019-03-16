---
title: Cmdlet 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058039"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="d770c-102">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="d770c-102">Cmdlet Samples</span></span>

<span data-ttu-id="d770c-103">本部分介绍 Windows PowerShell 2.0 SDK 中提供的示例代码。</span><span class="sxs-lookup"><span data-stu-id="d770c-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="d770c-104">可以将代码复制从主题中本部分中，或打开随 SDK 一起安装的源文件。</span><span class="sxs-lookup"><span data-stu-id="d770c-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="d770c-105">[Windows PowerShell 2.0 软件开发工具包 (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560)提供自述文件、 源文件，以及每个示例的 Visual Studio 项目文件。</span><span class="sxs-lookup"><span data-stu-id="d770c-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="d770c-106">已安装 sdk，可以找到下面的示例`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`文件夹。</span><span class="sxs-lookup"><span data-stu-id="d770c-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d770c-107">本部分内容</span><span class="sxs-lookup"><span data-stu-id="d770c-107">In This Section</span></span>

<span data-ttu-id="d770c-108">[GetProcessSample01 示例](./getprocesssample01-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="d770c-109">[GetProcessSample02 示例](./getprocesssample02-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="d770c-110">它提供了可用于指定要检索的进程的名称参数。</span><span class="sxs-lookup"><span data-stu-id="d770c-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="d770c-111">[GetProcessSample03 示例](./getprocesssample03-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="d770c-112">它提供了可接受管道中的对象或从一个对象，其属性名称为参数名称相同的属性值的名称参数。</span><span class="sxs-lookup"><span data-stu-id="d770c-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="d770c-113">[GetProcessSample04 示例](./getprocesssample04-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="d770c-114">如果在检索进程时发生错误，它会生成一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="d770c-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="d770c-115">[GetProcessSample05 示例](./getprocesssample05-sample.md)此示例演示 Get-proc cmdlet 的完整版本。</span><span class="sxs-lookup"><span data-stu-id="d770c-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="d770c-116">[StopProcessSample01 示例](./stopprocesssample01-sample.md)此示例演示如何编写一个 cmdlet，它会尝试停止进程之前, 请求用户反馈以及如何实现`PassThru`指示用户希望该 cmdlet 返回的参数对象。</span><span class="sxs-lookup"><span data-stu-id="d770c-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="d770c-117">[StopProcessSample02 示例](./stopprocesssample02-sample.md)此示例演示如何编写写入 verbose、 debug 和警告消息，同时在本地计算机上停止进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="d770c-118">[StopProcessSample03 示例](./stopprocesssample03-sample.md)此示例演示如何编写的 cmdlet 的参数的别名，并且支持通配符字符。</span><span class="sxs-lookup"><span data-stu-id="d770c-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="d770c-119">[StopProcessSample04 示例](./stopprocesssample04-sample.md)此示例演示如何编写声明参数集，指定默认参数集，它可以接受输入的对象的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d770c-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="d770c-120">[Events01 示例](./events01-sample.md)此示例演示如何创建 cmdlet 引发的事件，则允许用户注册[System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。</span><span class="sxs-lookup"><span data-stu-id="d770c-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="d770c-121">此 cmdlet 的用户可以例如，注册特定目录下创建一个文件时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d770c-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="d770c-122">此示例从派生[Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基类。</span><span class="sxs-lookup"><span data-stu-id="d770c-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d770c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d770c-123">See Also</span></span>

[<span data-ttu-id="d770c-124">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d770c-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
