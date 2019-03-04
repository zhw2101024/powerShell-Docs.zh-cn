---
title: 类型的 Cmdlet 的输出 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853923"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="579d4-102">类型的 cmdlet 的输出</span><span class="sxs-lookup"><span data-stu-id="579d4-102">Types of cmdlet output</span></span>

<span data-ttu-id="579d4-103">PowerShell 提供了几种方法可以调用的 cmdlet 以生成输出。</span><span class="sxs-lookup"><span data-stu-id="579d4-103">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="579d4-104">这些方法使用特定操作将其输出写入到特定的数据流，如数据流的成功或错误数据流。</span><span class="sxs-lookup"><span data-stu-id="579d4-104">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="579d4-105">本指南介绍了类型的输出和用于生成它们的方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-105">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="579d4-106">类型的输出</span><span class="sxs-lookup"><span data-stu-id="579d4-106">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="579d4-107">成功输出</span><span class="sxs-lookup"><span data-stu-id="579d4-107">Success output</span></span>

<span data-ttu-id="579d4-108">Cmdlet 返回一个对象，可以由管道中的下一个命令处理，可报告成功。</span><span class="sxs-lookup"><span data-stu-id="579d4-108">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="579d4-109">该 cmdlet 成功执行其操作后，该 cmdlet 会调用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-109">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="579d4-110">我们建议您调用此方法，而不是[System.Console.WriteLine](/dotnet/api/System.Console.WriteLine)或[System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-110">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="579d4-111">你可以提供**PassThru**切换通常不会返回对象的 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="579d4-111">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="579d4-112">当**PassThru**在命令行指定开关参数，则该 cmdlet 需要返回的对象。</span><span class="sxs-lookup"><span data-stu-id="579d4-112">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="579d4-113">有关具有 cmdlet 的示例**PassThru**参数，请参阅[Add-history](/powershell/module/Microsoft.PowerShell.Core/Add-History)。</span><span class="sxs-lookup"><span data-stu-id="579d4-113">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="579d4-114">错误输出</span><span class="sxs-lookup"><span data-stu-id="579d4-114">Error output</span></span>

<span data-ttu-id="579d4-115">Cmdlet 会报告的错误。</span><span class="sxs-lookup"><span data-stu-id="579d4-115">Cmdlets can report errors.</span></span> <span data-ttu-id="579d4-116">发生终止错误时，该 cmdlet 将引发异常。</span><span class="sxs-lookup"><span data-stu-id="579d4-116">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="579d4-117">发生非终止错误时，该 cmdlet 将调用[System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法以将错误记录发送到错误数据流。</span><span class="sxs-lookup"><span data-stu-id="579d4-117">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="579d4-118">有关错误报告的详细信息，请参阅[错误报告概念](./error-reporting-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="579d4-118">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="579d4-119">详细输出</span><span class="sxs-lookup"><span data-stu-id="579d4-119">Verbose output</span></span>

<span data-ttu-id="579d4-120">Cmdlet 可以提供有用信息对您在该 cmdlet 正在正确处理记录时通过调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-120">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="579d4-121">此方法将生成详细消息，指示如何继续下一步操作。</span><span class="sxs-lookup"><span data-stu-id="579d4-121">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="579d4-122">默认情况下不显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="579d4-122">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="579d4-123">您可以指定**Verbose**参数时运行该 cmdlet 来显示这些邮件。</span><span class="sxs-lookup"><span data-stu-id="579d4-123">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="579d4-124">**详细**是一个常见的参数，可供所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="579d4-124">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="579d4-125">进度输出</span><span class="sxs-lookup"><span data-stu-id="579d4-125">Progress output</span></span>

<span data-ttu-id="579d4-126">该 cmdlet 执行任务要花很长时间才能完成，如将目录以递归方式复制时，Cmdlet 可以向您提供进度信息。</span><span class="sxs-lookup"><span data-stu-id="579d4-126">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="579d4-127">若要显示进度信息 cmdlet 调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-127">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="579d4-128">调试输出</span><span class="sxs-lookup"><span data-stu-id="579d4-128">Debug output</span></span>

<span data-ttu-id="579d4-129">Cmdlet 可以提供故障排除的 cmdlet 代码时很有用的调试消息。</span><span class="sxs-lookup"><span data-stu-id="579d4-129">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="579d4-130">若要显示调试信息的 cmdlet 调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-130">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="579d4-131">默认情况下不显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="579d4-131">By default, debug messages are not displayed.</span></span> <span data-ttu-id="579d4-132">您可以指定**调试**参数时运行该 cmdlet 来显示这些邮件。</span><span class="sxs-lookup"><span data-stu-id="579d4-132">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="579d4-133">**调试**是一个常见的参数，可供所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="579d4-133">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="579d4-134">警告输出</span><span class="sxs-lookup"><span data-stu-id="579d4-134">Warning output</span></span>

<span data-ttu-id="579d4-135">Cmdlet 可显示警告消息，通过调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-135">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="579d4-136">默认情况下，会显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="579d4-136">By default, warning messages are displayed.</span></span> <span data-ttu-id="579d4-137">但是，可以通过配置警告消息`$WarningPreference`变量或通过使用**Verbose**并**调试**时调用该 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="579d4-137">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="579d4-138">显示输出</span><span class="sxs-lookup"><span data-stu-id="579d4-138">Displaying output</span></span>

<span data-ttu-id="579d4-139">对于所有写入方法调用，由特定的运行时变量确定显示内容。</span><span class="sxs-lookup"><span data-stu-id="579d4-139">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="579d4-140">例外情况是[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="579d4-140">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="579d4-141">通过使用这些变量，可以进行适当的在代码中编写正确的位置的调用，而不用担心，或者如果应显示的输出。</span><span class="sxs-lookup"><span data-stu-id="579d4-141">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="579d4-142">访问主机应用程序的输出功能</span><span class="sxs-lookup"><span data-stu-id="579d4-142">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="579d4-143">此外可以设计用于直接通过 PowerShell 运行时访问主机应用程序的输出功能的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="579d4-143">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="579d4-144">使用主机提供的 PowerShell 而不是 Api [System.Console](/dotnet/api/System.Console)或[System.Windows.Forms](/dotnet/api/System.Windows.Forms)可确保你的 cmdlet 将使用不同主机。</span><span class="sxs-lookup"><span data-stu-id="579d4-144">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="579d4-145">例如： **powershell.exe**控制台主机**powershell_ise.exe**图形主机、 PowerShell 远程处理主机和第三方主机。</span><span class="sxs-lookup"><span data-stu-id="579d4-145">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="579d4-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="579d4-146">See also</span></span>

[<span data-ttu-id="579d4-147">错误报告概念</span><span class="sxs-lookup"><span data-stu-id="579d4-147">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="579d4-148">Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="579d4-148">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="579d4-149">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="579d4-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)