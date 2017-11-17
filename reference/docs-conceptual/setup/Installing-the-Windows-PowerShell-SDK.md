---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "安装 Windows PowerShell SDK"
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: c6acba828e469e716c80603ec2432176652a7280
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="e9f2a-103">安装 Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e9f2a-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="e9f2a-104">以下主题介绍了如何在不同版本的 Windows 中安装 PowerShell SDK。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="e9f2a-105">安装用于 Windows 8 和 Windows Server 2012 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="e9f2a-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="e9f2a-106">Windows PowerShell 3.0 随 Windows 8 和 Windows Server 2012 自动安装。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="e9f2a-107">此外，可以下载并安装 Windows PowerShell 3.0 的引用程序集作为 Windows 8 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="e9f2a-108">你可以使用这些程序集为 Windows PowerShell 3.0 编写 cmdlet、提供商和主机程序。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="e9f2a-109">在 Windows 8 中安装 Windows SDK 时，将在引用程序集文件夹（位于 \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0）中自动安装 Windows PowerShell 程序集。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="e9f2a-110">有关详细信息，请参阅 [Windows 8 SDK 下载站点](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="e9f2a-111">此开发中心还提供了 Windows PowerShell 的代码示例。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="e9f2a-112">有关详细信息，请参阅[开发人员中心站点](http://code.msdn.microsoft.com/windowsdesktop/)上的桌面代码示例页。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="e9f2a-113">此外，Windows PowerShell 3.0 与 Windows PowerShell 2.0 SDK 是向后兼容，后者包括大量代码示例。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="e9f2a-114">有关如何下载 Windows PowerShell 2.0 SDK 的详细信息，请参阅后文。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="e9f2a-115">（请注意，虽然 2.0 代码示例与 Windows 8 和 Windows PowerShell 3.0 兼容，但不能在 Windows 8 平台上安装 Windows PowerShell 2.0。）</span><span class="sxs-lookup"><span data-stu-id="e9f2a-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="e9f2a-116">安装用于 Windows 7 和 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="e9f2a-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="e9f2a-117">Windows 7 和 Windows Server 2008 R2 将自动安装 PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="e9f2a-118">此外，你还可以在这些系统上安装 PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="e9f2a-119">（有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md)。）。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="e9f2a-120">如上所述，你还可以在 Windows 7 和 Windows Server 2008 R2 中安装 Windows 8 SDK。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="e9f2a-121">安装用于 Windows 7、Vista、XP、Server 2003 和 Server 2008 的 Windows PowerShell 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="e9f2a-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="e9f2a-122">Windows PowerShell 2.0 SDK 提供了用于编写 cmdlet、提供程序和托管应用程序所需的引用程序集，还提供了 C# 示例代码，开始编写代码时你可以使用此示例代码作为起点。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="e9f2a-123">若要安装此 SDK，请参阅 [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611)。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="e9f2a-124">引用程序集</span><span class="sxs-lookup"><span data-stu-id="e9f2a-124">Reference assemblies</span></span>

<span data-ttu-id="e9f2a-125">默认情况下，引用程序集安装在以下位置：`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="e9f2a-126">**请注意**：无法将针对 Windows PowerShell 2.0 程序集编译的代码加载到 Windows PowerShell 1.0 安装中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="e9f2a-127">但可以将针对 Windows PowerShell 1.0 程序集编译的代码加载到 Windows PowerShell 2.0 安装中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="e9f2a-128">示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-128">Samples</span></span>

<span data-ttu-id="e9f2a-129">默认情况下，代码示例安装在以下位置：`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="e9f2a-130">以下部分提供对每个示例的作用的简要描述。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="e9f2a-131">Cmdlet 示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-131">Cmdlet samples</span></span>
<span data-ttu-id="e9f2a-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-132">**GetProcessSample01**</span></span>

<span data-ttu-id="e9f2a-133">演示如何编写获取本地计算机上所有进程的简单 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="e9f2a-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-134">**GetProcessSample02**</span></span>

<span data-ttu-id="e9f2a-135">演示如何将参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="e9f2a-136">cmdlet 可接受一个或多个进程名称，并返回匹配的进程。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="e9f2a-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-137">**GetProcessSample03**</span></span>

<span data-ttu-id="e9f2a-138">演示如何添加接受来自管道的输入的参数。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="e9f2a-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-139">**GetProcessSample04**</span></span>

<span data-ttu-id="e9f2a-140">演示如何处理非终止错误。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="e9f2a-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-141">**GetProcessSample05**</span></span>

<span data-ttu-id="e9f2a-142">演示如何显示指定进程的列表。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="e9f2a-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-143">**SelectObject**</span></span>

<span data-ttu-id="e9f2a-144">演示如何编写筛选器以仅选择特定对象。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="e9f2a-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-145">**SelectString**</span></span>

<span data-ttu-id="e9f2a-146">演示如何搜索指定模式的文件。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="e9f2a-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-147">**StopProcessSample01**</span></span>

<span data-ttu-id="e9f2a-148">演示如何实现 *PassThru* 参数，以及如何通过对 [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) 和 [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) 方法的调用请求用户反馈。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="e9f2a-149">当用户要强制 cmdlet 返回对象时，应指定 *PassThru* 参数，</span><span class="sxs-lookup"><span data-stu-id="e9f2a-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="e9f2a-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-150">**StopProcessSample02**</span></span>

<span data-ttu-id="e9f2a-151">演示如何停止特定进程。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="e9f2a-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-152">**StopProcessSample03**</span></span>

<span data-ttu-id="e9f2a-153">演示如何声明参数的别名以及如何支持通配符。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="e9f2a-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-154">**StopProcessSample04**</span></span>

<span data-ttu-id="e9f2a-155">演示如何声明参数集（即 cmdlet 将其作为输入的对象）以及如何指定要使用的默认参数集。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="e9f2a-156">远程示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-156">Remoting samples</span></span>

<span data-ttu-id="e9f2a-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="e9f2a-158">演示如何创建用于建立远程连接的远程运行空间。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="e9f2a-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="e9f2a-160">演示如何构造远程运行空间池以及如何通过使用此池同时运行多个命令。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="e9f2a-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-161">**Serialization01**</span></span>

<span data-ttu-id="e9f2a-162">演示如何查看现有 .NET 类，并确保跨序列化/反序列化保存此类的所选公共属性中的信息。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="e9f2a-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-163">**Serialization02**</span></span>

<span data-ttu-id="e9f2a-164">演示如何查看现有.NET 类，并确保当信息在类的公共属性中不可用时，跨序列化/反序列化保存此类的实例中的信息。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="e9f2a-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-165">**Serialization03**</span></span>

<span data-ttu-id="e9f2a-166">演示如何查看现有 .NET 类，并确保将此类和派生类的实例反序列化（解除冻结）为实时 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="e9f2a-167">事件示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-167">Event samples</span></span>

<span data-ttu-id="e9f2a-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-168">**Event01**</span></span>

<span data-ttu-id="e9f2a-169">演示如何通过从 ObjectEventRegistrationBase 派生创建用于事件注册的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="e9f2a-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-170">**Event02**</span></span>

<span data-ttu-id="e9f2a-171">演示如何接收在远程计算机上生成的 Windows PowerShell 事件的通知。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="e9f2a-172">它使用通过 [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) 类公开的 PSEventReceived 事件。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="e9f2a-173">托管应用程序示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-173">Hosting application samples</span></span>

<span data-ttu-id="e9f2a-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-174">**Runspace01**</span></span>

<span data-ttu-id="e9f2a-175">演示如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 类来同步运行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="e9f2a-176">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet 返回在本地计算机上运行的每个进程的 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 对象。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="e9f2a-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-177">**Runspace02**</span></span>

<span data-ttu-id="e9f2a-178">演示如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 类来同步运行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) 和 [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="e9f2a-179">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet 返回在本地计算机上运行的每个进程的 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 对象，而 Sort-Object 基于这些对象的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 属性对其进行排序。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="e9f2a-180">使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控件显示这些命令的结果。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="e9f2a-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-181">**Runspace03**</span></span>

<span data-ttu-id="e9f2a-182">演示如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 类来同步运行脚本，以及如何处理非终止错误。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="e9f2a-183">该脚本可接收一系列进程名称，然后检索这些进程。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="e9f2a-184">脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="e9f2a-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-185">**Runspace04**</span></span>

<span data-ttu-id="e9f2a-186">演示如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 类来运行命令，以及如何捕获运行命令时引发的终止错误。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="e9f2a-187">运行了两个命令，最后一个命令传递给了一个无效的参数。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="e9f2a-188">因此，未返回对象并引发了终止错误。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="e9f2a-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-189">**Runspace05**</span></span>

<span data-ttu-id="e9f2a-190">演示如何将管理单元添加到 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 对象，使该管理单元的 cmdlet 在运行空间打开时可用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="e9f2a-191">管理单元提供通过使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象同步运行的 Get-Proc cmdlet（由 [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx) 定义）。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e9f2a-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-192">**Runspace06**</span></span>

<span data-ttu-id="e9f2a-193">演示如何将模块添加到 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 对象，以便在打开运行空间时加载此模块。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="e9f2a-194">模块提供 Get-Proc cmdlet（由 [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx) 定义），此 cmdlet 通过使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象同步运行。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e9f2a-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-195">**Runspace07**</span></span>

<span data-ttu-id="e9f2a-196">演示如何通过使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象，创建运行空间，然后使用此运行空间同步运行两个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e9f2a-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-197">**Runspace08**</span></span>

<span data-ttu-id="e9f2a-198">演示如何将命令和参数添加到 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象的管道，以及如何同步运行命令。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="e9f2a-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-199">**Runspace09**</span></span>

<span data-ttu-id="e9f2a-200">演示如何将脚本添加到 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象的管道以及如何异步运行脚本。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="e9f2a-201">使用事件处理脚本的输出。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="e9f2a-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-202">**Runspace10**</span></span>

<span data-ttu-id="e9f2a-203">演示如何创建默认初始会话状态、如何将 cmdlet 添加到 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)、如何创建使用初始会话状态的运行空间以及如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 对象运行命令。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e9f2a-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-204">**Runspace11**</span></span>

<span data-ttu-id="e9f2a-205">演示如何使用 [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) 类创建调用现有 cmdlet 但限制可用参数集的代理命令。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="e9f2a-206">然后，代理命令被添加到用来创建受限运行空间的初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="e9f2a-207">这意味着用户只能通过该代理命令使用该 cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="e9f2a-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-208">**PowerShell01**</span></span>

<span data-ttu-id="e9f2a-209">演示如何使用 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 对象创建受约束的运行空间。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="e9f2a-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-210">**PowerShell02**</span></span>

<span data-ttu-id="e9f2a-211">演示如何使用运行空间池同时运行多个命令。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="e9f2a-212">主机示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-212">Host samples</span></span>

<span data-ttu-id="e9f2a-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-213">**Host01**</span></span>

<span data-ttu-id="e9f2a-214">演示如何实现使用自定义主机的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="e9f2a-215">在此示例中，创建使用自定义主机的运行空间，然后 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API 用于运行调用“exit”的脚本。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="e9f2a-216">主机应用程序随后查看脚本输出并打印出结果。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="e9f2a-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-217">**Host02**</span></span>

<span data-ttu-id="e9f2a-218">演示如何编写结合使用 Windows PowerShell 运行时与自定义主机实现的主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="e9f2a-219">主机应用程序将主机区域性设置为 German，运行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet 并显示结果（使用 pwrsh.exe 可查看这些结果），然后打印出德语形式的当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="e9f2a-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-220">**Host03**</span></span>

<span data-ttu-id="e9f2a-221">演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="e9f2a-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-222">**Host04**</span></span>

<span data-ttu-id="e9f2a-223">演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e9f2a-224">此主机应用程序还支持显示允许用户指定多个选项的提示。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="e9f2a-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-225">**Host05**</span></span>

<span data-ttu-id="e9f2a-226">演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e9f2a-227">此主机应用程序还支持通过使用 [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) 和 [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlet 调用远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="e9f2a-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-228">**Host06**</span></span>

<span data-ttu-id="e9f2a-229">演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取并执行命令，然后将结果显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e9f2a-230">此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="e9f2a-231">提供程序示例</span><span class="sxs-lookup"><span data-stu-id="e9f2a-231">Provider samples</span></span>

<span data-ttu-id="e9f2a-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="e9f2a-233">演示如何声明直接派生自 [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) 类的提供程序类。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="e9f2a-234">仅出于完整性考虑而在此处包含此项。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-234">It is included here only for completeness.</span></span>

<span data-ttu-id="e9f2a-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="e9f2a-236">演示如何覆盖 [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) 和 [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) 方法以支持对 New-PSDrive 和 Remove-PSDrive cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="e9f2a-237">此示例中的提供程序类派生自 [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) 类。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e9f2a-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="e9f2a-239">演示如何覆盖 [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) 和 [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) 方法以支持对 Get-Item 和 Set-Item cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="e9f2a-240">此示例中的提供程序类派生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 类。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e9f2a-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="e9f2a-242">演示如何覆盖容器方法以支持对 Copy-Item、Get-ChildItem、New-Item 和 Remove-Item cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="e9f2a-243">当数据存储区包含属于容器的项时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="e9f2a-244">容器是包含公用父项下的子项的组。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="e9f2a-245">此示例中的提供程序类派生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 类。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e9f2a-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="e9f2a-247">演示如何覆盖容器方法以支持对 Move-Item 和 Join-Path cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="e9f2a-248">当用户需要移动容器中的项时，如果数据存储区包含嵌套的容器，则应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="e9f2a-249">此示例中的提供程序类派生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e9f2a-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="e9f2a-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="e9f2a-251">演示如何覆盖内容方法以支持对 Clear-Content、Get-Content 和 Set-Content cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="e9f2a-252">当用户需要管理数据存储区中的项的内容时，应实现这些方法。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="e9f2a-253">此示例中的提供程序派生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 类，并实现 [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) 接口。</span><span class="sxs-lookup"><span data-stu-id="e9f2a-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>

