---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 运行远程命令
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482873"
---
# <a name="running-remote-commands"></a><span data-ttu-id="b8652-103">运行远程命令</span><span class="sxs-lookup"><span data-stu-id="b8652-103">Running Remote Commands</span></span>

<span data-ttu-id="b8652-104">你可以使用单个 Windows PowerShell 命令在一台或数百台计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="b8652-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="b8652-105">Windows PowerShell 通过使用各种技术（包括 WMI、RPC 和 WS-Management）支持远程计算。</span><span class="sxs-lookup"><span data-stu-id="b8652-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="b8652-106">在 PowerShell Core 中进行远程处理</span><span class="sxs-lookup"><span data-stu-id="b8652-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="b8652-107">PowerShell 在 Windows、macOS 和 Linux 上的新版本 PowerShell Core 支持 WMI、WS-Management 和 SSH 远程处理。</span><span class="sxs-lookup"><span data-stu-id="b8652-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="b8652-108">（不再支持 RPC。）</span><span class="sxs-lookup"><span data-stu-id="b8652-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="b8652-109">有关设置详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="b8652-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="b8652-110">[在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="b8652-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="b8652-111">[在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="b8652-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="b8652-112">无需配置即可进行远程处理</span><span class="sxs-lookup"><span data-stu-id="b8652-112">Remoting Without Configuration</span></span>

<span data-ttu-id="b8652-113">许多 Windows PowerShell cmdlet 都具有 ComputerName 参数，此参数可使你在一台或多台远程计算机上收集数据和更改设置。</span><span class="sxs-lookup"><span data-stu-id="b8652-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="b8652-114">它们使用各种通信技术，并且许多 cmdlet 在 Windows PowerShell 支持的所有 Windows 操作系统上都有效，而无需任何特殊配置。</span><span class="sxs-lookup"><span data-stu-id="b8652-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="b8652-115">这些 cmdlet 包括：</span><span class="sxs-lookup"><span data-stu-id="b8652-115">These cmdlets include:</span></span>

* [<span data-ttu-id="b8652-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="b8652-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="b8652-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="b8652-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="b8652-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="b8652-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="b8652-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="b8652-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="b8652-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="b8652-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="b8652-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="b8652-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="b8652-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="b8652-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="b8652-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="b8652-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="b8652-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="b8652-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="b8652-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b8652-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="b8652-126">通常情况下，支持无需特殊配置即可进行远程处理的 cmdlet 具有 ComputerName 参数，但不具有 Session 参数。</span><span class="sxs-lookup"><span data-stu-id="b8652-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="b8652-127">若要在会话中查找这些 cmdlet，请键入：</span><span class="sxs-lookup"><span data-stu-id="b8652-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="b8652-128">Windows PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="b8652-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="b8652-129">Windows PowerShell 远程处理，它使用 WS-Management 协议，并且使你可以在一台或多台远程计算机上运行任何 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b8652-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="b8652-130">它使你可以建立持久连接、启动 1:1 交互会话并在多台计算机上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b8652-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="b8652-131">若要使用 Windows PowerShell 远程处理，必须配置远程计算机以进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="b8652-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="b8652-132">有关详细信息（包括说明），请参阅[关于远程要求](https://technet.microsoft.com/library/dd315349.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b8652-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="b8652-133">配置了 Windows PowerShell 远程处理后，有许多远程处理策略可供你使用。</span><span class="sxs-lookup"><span data-stu-id="b8652-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="b8652-134">此文档的其余部分只列出了其中的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8652-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="b8652-135">有关详细信息，请参阅 [About Remote（关于远程）](https://technet.microsoft.com/library/dd347744.aspx)和 [About Remote FAQ（关于远程 FAQ）](https://technet.microsoft.com/library/dd347744.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b8652-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="b8652-136">启动交互会话</span><span class="sxs-lookup"><span data-stu-id="b8652-136">Start an Interactive Session</span></span>

<span data-ttu-id="b8652-137">若要使用单台远程计算机启动交互会话，请使用 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8652-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="b8652-138">例如，若要使用 Server01 远程计算器启动交互会话，请键入：</span><span class="sxs-lookup"><span data-stu-id="b8652-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="b8652-139">命令提示符更改为显示你连接到的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="b8652-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="b8652-140">此后，你在提示符中键入的任何命令都将在远程计算机上运行，并且结果将显示在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="b8652-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="b8652-141">若要结束交互会话，请键入：</span><span class="sxs-lookup"><span data-stu-id="b8652-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="b8652-142">有关 Enter-PSSession 和 Exit-PSSession cmdlet 的详细信息，请参阅 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) 和 [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478)。</span><span class="sxs-lookup"><span data-stu-id="b8652-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="b8652-143">运行远程命令</span><span class="sxs-lookup"><span data-stu-id="b8652-143">Run a Remote Command</span></span>

<span data-ttu-id="b8652-144">若要在一台或多台远程计算机上运行任何命令，请使用 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8652-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="b8652-145">例如，若要在 Server01 和 Server02 远程计算机上运行 [Get-UICulture ](https://go.microsoft.com/fwlink/?LinkId=821806) 命令，请键入：</span><span class="sxs-lookup"><span data-stu-id="b8652-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="b8652-146">输出将返回到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="b8652-146">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="b8652-147">有关 Invoke-Command cmdlet 的详细信息，请参阅 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。</span><span class="sxs-lookup"><span data-stu-id="b8652-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="b8652-148">运行脚本</span><span class="sxs-lookup"><span data-stu-id="b8652-148">Run a Script</span></span>

<span data-ttu-id="b8652-149">若要在一台或多台远程计算机上运行脚本，请使用 Invoke-Command cmdlet 的 FilePath 参数。</span><span class="sxs-lookup"><span data-stu-id="b8652-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="b8652-150">该脚本必须在你的本地计算机上或可由其访问。</span><span class="sxs-lookup"><span data-stu-id="b8652-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="b8652-151">结果将返回到你的本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b8652-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="b8652-152">例如，以下命令在 Server01 和 Server02 远程计算机上运行 DiskCollect.ps1 脚本。</span><span class="sxs-lookup"><span data-stu-id="b8652-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="b8652-153">有关 Invoke-Command cmdlet 的详细信息，请参阅 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。</span><span class="sxs-lookup"><span data-stu-id="b8652-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="b8652-154">建立持久连接</span><span class="sxs-lookup"><span data-stu-id="b8652-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="b8652-155">若要运行一系列共享数据的相关命令，请在远程计算机上创建会话，然后使用 Invoke-Command cmdlet 在你创建的会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="b8652-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="b8652-156">若要创建远程会话，请使用 New-PSSession cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8652-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="b8652-157">例如，以下命令在 Server01 计算机上创建远程会话，在 Server02 计算机上创建另一个远程会话。</span><span class="sxs-lookup"><span data-stu-id="b8652-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="b8652-158">它将会话对象保存在 $s 变量中。</span><span class="sxs-lookup"><span data-stu-id="b8652-158">It saves the session objects in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="b8652-159">建立会话后，你可以在这些会话中运行任何命令。</span><span class="sxs-lookup"><span data-stu-id="b8652-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="b8652-160">此外，由于会话是持久的，因此你可以在一个命令中收集数据，在后续命令中使用它。</span><span class="sxs-lookup"><span data-stu-id="b8652-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="b8652-161">例如，下面的命令在 $s 变量中的会话中运行 Get-Hotfix 命令，并且它将结果保存在 $h 变量中。</span><span class="sxs-lookup"><span data-stu-id="b8652-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="b8652-162">将在 $s 中的每个会话中创建 $h 变量，但它不会存在于本地会话中。</span><span class="sxs-lookup"><span data-stu-id="b8652-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="b8652-163">现在，你可以在后续命令中使用 $h 变量中的数据，例如以下命令。</span><span class="sxs-lookup"><span data-stu-id="b8652-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="b8652-164">结果将显示在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="b8652-164">The results are displayed on the local computer.</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="b8652-165">高级远程处理</span><span class="sxs-lookup"><span data-stu-id="b8652-165">Advanced Remoting</span></span>

<span data-ttu-id="b8652-166">Windows PowerShell 远程管理就在此处开始。</span><span class="sxs-lookup"><span data-stu-id="b8652-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="b8652-167">通过使用随 Windows PowerShell 一起安装的 cmdlet，你可以从本地和远程端点建立和配置远程会话、创建自定义和受限制的会话、允许用户从实际在远程会话上隐式运行的远程会话中导入命令、配置远程会话的安全性等。</span><span class="sxs-lookup"><span data-stu-id="b8652-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="b8652-168">为了便于远程配置，Windows PowerShell 包含了 WSMan 提供程序。</span><span class="sxs-lookup"><span data-stu-id="b8652-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="b8652-169">提供程序创建的 WSMAN: 驱动器使你可以在本地计算机和远程计算机上的配置设置层次结构之间导航。</span><span class="sxs-lookup"><span data-stu-id="b8652-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="b8652-170">有关 WSMan 提供程序的详细信息，请参阅 [WSMan 提供程序](https://technet.microsoft.com/library/dd819476.aspx)和[关于 WS-Management Cmdlet](https://technet.microsoft.com/library/dd819481.aspx)，或在 Windows PowerShell 控制台中键入“Get-Help wsman”。</span><span class="sxs-lookup"><span data-stu-id="b8652-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="b8652-171">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="b8652-171">For more information, see:</span></span>

- [<span data-ttu-id="b8652-172">有关远程的常见问题解答</span><span class="sxs-lookup"><span data-stu-id="b8652-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="b8652-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8652-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="b8652-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8652-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="b8652-175">有关远程处理错误的帮助，请参阅 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b8652-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8652-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8652-176">See Also</span></span>

- [<span data-ttu-id="b8652-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b8652-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="b8652-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="b8652-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="b8652-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="b8652-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="b8652-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="b8652-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="b8652-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b8652-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="b8652-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b8652-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="b8652-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b8652-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="b8652-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8652-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="b8652-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8652-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="b8652-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8652-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="b8652-187">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="b8652-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md