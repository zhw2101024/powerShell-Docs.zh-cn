---
title: Cmdlet 输出的类型 |Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369286"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="a9120-102">Cmdlet 输出的类型</span><span class="sxs-lookup"><span data-stu-id="a9120-102">Types of cmdlet output</span></span>

<span data-ttu-id="a9120-103">PowerShell 提供多种方法，这些方法可由 cmdlet 调用以生成输出。</span><span class="sxs-lookup"><span data-stu-id="a9120-103">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="a9120-104">这些方法使用特定操作将其输出写入特定数据流，如成功数据流或错误数据流。</span><span class="sxs-lookup"><span data-stu-id="a9120-104">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="a9120-105">本文介绍输出类型以及用于生成它们的方法。</span><span class="sxs-lookup"><span data-stu-id="a9120-105">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="a9120-106">输出类型</span><span class="sxs-lookup"><span data-stu-id="a9120-106">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="a9120-107">成功输出</span><span class="sxs-lookup"><span data-stu-id="a9120-107">Success output</span></span>

<span data-ttu-id="a9120-108">Cmdlet 可以通过返回可由管道中的下一个命令处理的对象来报告成功。</span><span class="sxs-lookup"><span data-stu-id="a9120-108">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="a9120-109">Cmdlet 成功执行了其操作后，该 cmdlet 将调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="a9120-109">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="a9120-110">我们建议你调用此方法，而不是调用[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法或[方法的方法](/dotnet/api/System.Console.WriteLine)。</span><span class="sxs-lookup"><span data-stu-id="a9120-110">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="a9120-111">你可以为不返回对象的 cmdlet 提供**PassThru**交换机参数。</span><span class="sxs-lookup"><span data-stu-id="a9120-111">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="a9120-112">当在命令行中指定**PassThru**交换机参数时，系统将要求 cmdlet 返回对象。</span><span class="sxs-lookup"><span data-stu-id="a9120-112">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="a9120-113">有关具有**PassThru**参数的 cmdlet 的示例，请参阅[添加-历史记录](/powershell/module/Microsoft.PowerShell.Core/Add-History)。</span><span class="sxs-lookup"><span data-stu-id="a9120-113">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="a9120-114">错误输出</span><span class="sxs-lookup"><span data-stu-id="a9120-114">Error output</span></span>

<span data-ttu-id="a9120-115">Cmdlet 可以报告错误。</span><span class="sxs-lookup"><span data-stu-id="a9120-115">Cmdlets can report errors.</span></span> <span data-ttu-id="a9120-116">当发生终止错误时，cmdlet 会引发异常。</span><span class="sxs-lookup"><span data-stu-id="a9120-116">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="a9120-117">当发生非终止错误时，该 cmdlet 将调用[CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，将错误记录发送到错误数据流。</span><span class="sxs-lookup"><span data-stu-id="a9120-117">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="a9120-118">有关错误报告的详细信息，请参阅[错误报告概念](./error-reporting-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="a9120-118">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="a9120-119">详细输出</span><span class="sxs-lookup"><span data-stu-id="a9120-119">Verbose output</span></span>

<span data-ttu-id="a9120-120">Cmdlet 可以通过调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法正确地处理记录，为你提供有用的信息。</span><span class="sxs-lookup"><span data-stu-id="a9120-120">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="a9120-121">方法会生成详细消息，指示操作的执行方式。</span><span class="sxs-lookup"><span data-stu-id="a9120-121">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="a9120-122">默认情况下，不显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-122">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="a9120-123">可以在运行 cmdlet 时指定**详细**参数，以显示这些消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-123">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="a9120-124">**详细**是适用于所有 cmdlet 的通用参数。</span><span class="sxs-lookup"><span data-stu-id="a9120-124">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="a9120-125">进度输出</span><span class="sxs-lookup"><span data-stu-id="a9120-125">Progress output</span></span>

<span data-ttu-id="a9120-126">当 cmdlet 执行需要很长时间才能完成的任务（例如，递归复制目录）时，cmdlet 可为你提供进度信息。</span><span class="sxs-lookup"><span data-stu-id="a9120-126">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="a9120-127">若要显示进度信息，cmdlet 将调用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="a9120-127">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="a9120-128">调试输出</span><span class="sxs-lookup"><span data-stu-id="a9120-128">Debug output</span></span>

<span data-ttu-id="a9120-129">Cmdlet 可以提供调试消息，这些消息对 cmdlet 代码进行疑难解答时非常有用。</span><span class="sxs-lookup"><span data-stu-id="a9120-129">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="a9120-130">若要显示调试信息，该 cmdlet 将调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="a9120-130">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="a9120-131">默认情况下，不显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-131">By default, debug messages are not displayed.</span></span> <span data-ttu-id="a9120-132">可以在运行 cmdlet 时指定**Debug**参数以显示这些消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-132">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="a9120-133">**Debug**是适用于所有 cmdlet 的通用参数。</span><span class="sxs-lookup"><span data-stu-id="a9120-133">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="a9120-134">警告输出</span><span class="sxs-lookup"><span data-stu-id="a9120-134">Warning output</span></span>

<span data-ttu-id="a9120-135">Cmdlet 可以通过调用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法来显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-135">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="a9120-136">默认情况下，会显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-136">By default, warning messages are displayed.</span></span> <span data-ttu-id="a9120-137">但是，你可以通过使用 `$WarningPreference` 变量或在调用 cmdlet 时使用**Verbose**和**Debug**参数来配置警告消息。</span><span class="sxs-lookup"><span data-stu-id="a9120-137">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="a9120-138">显示输出</span><span class="sxs-lookup"><span data-stu-id="a9120-138">Displaying output</span></span>

<span data-ttu-id="a9120-139">对于所有写方法调用，内容显示由特定的运行时变量确定。</span><span class="sxs-lookup"><span data-stu-id="a9120-139">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="a9120-140">[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法是异常的例外情况。</span><span class="sxs-lookup"><span data-stu-id="a9120-140">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="a9120-141">通过使用这些变量，你可以在代码中的正确位置进行适当的写入调用，而无需担心是否应显示输出。</span><span class="sxs-lookup"><span data-stu-id="a9120-141">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="a9120-142">访问主机应用程序的输出功能</span><span class="sxs-lookup"><span data-stu-id="a9120-142">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="a9120-143">你还可以设计 cmdlet，以通过 PowerShell 运行时直接访问主机应用程序的输出功能。</span><span class="sxs-lookup"><span data-stu-id="a9120-143">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="a9120-144">使用 PowerShell 提供的宿主 Api，而不是使用[system. 控制台](/dotnet/api/System.Console)或[System.web。窗体](/dotnet/api/System.Windows.Forms)可确保你的 cmdlet 可与各种主机一起使用。</span><span class="sxs-lookup"><span data-stu-id="a9120-144">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="a9120-145">例如： **ngen.exe**控制台主机、 **powershell_ise**图形主机、powershell 远程处理主机和第三方主机。</span><span class="sxs-lookup"><span data-stu-id="a9120-145">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9120-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9120-146">See also</span></span>

[<span data-ttu-id="a9120-147">错误报告概念</span><span class="sxs-lookup"><span data-stu-id="a9120-147">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="a9120-148">Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="a9120-148">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="a9120-149">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a9120-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)