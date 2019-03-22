---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: 使用 JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054673"
---
# <a name="using-jea"></a><span data-ttu-id="ca9e2-103">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="ca9e2-103">Using JEA</span></span>

> <span data-ttu-id="ca9e2-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ca9e2-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ca9e2-105">本主题介绍连接和使用 JEA 终结点的各种方式。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="ca9e2-106">以交互方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="ca9e2-106">Using JEA interactively</span></span>

<span data-ttu-id="ca9e2-107">如果你正在测试 JEA 配置或具有需要用户执行的简单任务，可以采用与进行常规 PowerShell 远程处理会话相同的方式使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="ca9e2-108">对于复杂的远程处理任务，建议改为使用[隐式远程处理](#using-jea-with-implicit-remoting)，允许用户在本地处理数据对象，以方便用户进行操作。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="ca9e2-109">以交互方式使用 JEA 需要提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="ca9e2-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="ca9e2-110">要连接到的计算机名称（可以是本地计算机）</span><span class="sxs-lookup"><span data-stu-id="ca9e2-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="ca9e2-111">在该计算机上注册的 JEA 终结点名称</span><span class="sxs-lookup"><span data-stu-id="ca9e2-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="ca9e2-112">该计算机有权访问 JEA 终结点的凭据</span><span class="sxs-lookup"><span data-stu-id="ca9e2-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="ca9e2-113">获取该信息后，可以使用 [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession) 开始 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="ca9e2-114">如果当前登录的帐户有权访问 JEA 终结点，则可以省略 `-Credential` 参数。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="ca9e2-115">PowerShell 提示更改为 `[localhost]: PS>` 时，你会知道自己正在与远程 JEA 会话交互。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="ca9e2-116">可以运行 `Get-Command` 检查哪些命令可用。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="ca9e2-117">你需要咨询管理员，了解可用参数或允许参数值是否存在任何限制。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="ca9e2-118">提醒一下，由于 JEA 会话在 NoLanguage 模式下运行，因此通常使用 PowerShell 的某些方式可能不适用。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="ca9e2-119">例如，你无法使用变量存储数据或检查从 cmdlet 返回的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="ca9e2-120">下面的示例展示了目前 PowerShell 的使用方式，以及使相同的命令在 NoLanguage 模式下工作的两种方法。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="ca9e2-121">对于增加此方法难度的更复杂的命令调用，请考虑使用包含所需功能的[隐式远程处理](#using-jea-with-implicit-remoting)或[创建自定义函数](role-capabilities.md#creating-custom-functions)。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="ca9e2-122">将 JEA 与隐式远程处理配合使用</span><span class="sxs-lookup"><span data-stu-id="ca9e2-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="ca9e2-123">PowerShell 支持备用远程处理模型，在此模型中，用户可以将代理 cmdlet 从远程计算机导入本地计算机，并且可以如同本地命令一样与之交互。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="ca9e2-124">这称为隐式远程处理，[这篇 *Hey, Scripting Guy!*《你好，脚本专家！》博客文章](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)中对此进行了详细介绍。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="ca9e2-125">当隐式远程处理配合 JEA 使用时特别有用，因为它允许在完整语言模式下使用 JEA cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="ca9e2-126">这意味着可以使用 Tab 自动补全和变量，操作对象，甚至使用本地脚本对 JEA 终结点更轻松地实现自动化。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="ca9e2-127">每当调用代理命令时，数据将发送到远程计算机上的 JEA 终结点并加以执行。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="ca9e2-128">隐式远程处理工作时，从现有 PowerShell 会话中导入 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="ca9e2-129">可以有选择性地选择使用所选字符串作为每个代理 cmdlet 名词的前缀，以区分哪些命令适用于远程系统。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="ca9e2-130">将创建包含所有代理命令的临时脚本模块，该模块可在本地 PowerShell 会话期间使用。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="ca9e2-131">由于默认 JEA cmdlet 中存在约束，某些系统可能无法导入整个 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="ca9e2-132">为避免这一问题，请向 `-CommandName` 参数显示提供名称，从 JEA 会话仅导入所需的命令。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="ca9e2-133">将来的更新会解决在受影响的系统上导入整个 JEA 会话方面的问题。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="ca9e2-134">如果由于默认 JEA 参数存在约束而无法导入 JEA 会话，可以按照以下步骤操作，从导入组中筛选出默认命令。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="ca9e2-135">你仍可使用 `Select-Object` 等命令 - 只需使用安装在计算机上的本地版本，而非 JEA 会话中的远程版本。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="ca9e2-136">还可以使用 [Export-pssession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession) 通过隐式远程处理保留代理 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="ca9e2-137">有关隐式远程处理的详细信息，请参阅 [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) 和 [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module) 的帮助文档。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="ca9e2-138">以编程方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="ca9e2-138">Using JEA programmatically</span></span>

<span data-ttu-id="ca9e2-139">JEA 还可用于自动化系统和用户应用程序，例如内部的支持人员应用和 Web 站点。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="ca9e2-140">该方法和生成与非约束 PowerShell 终结点进行会话的应用所用的方法相同，同时警告程序应该注意 JEA 将限制可在远程会话中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="ca9e2-141">对于简单的一次性任务，可以使用 [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) 来运行使用 JEA 的一组命令。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="ca9e2-142">若要检查连接到 JEA 会话时哪些命令可用，请运行 `Get-Command` 并循环访问结果以查看允许的参数。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="ca9e2-143">如果要生成 C# 应用，可以通过在 [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) 对象中指定配置名称来创建与 JEA 会话连接的 PowerShell 运行空间。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="ca9e2-144">将 JEA 与 PowerShell Direct 配合使用</span><span class="sxs-lookup"><span data-stu-id="ca9e2-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="ca9e2-145">Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession) 功能，以便 Hyper-V 管理员可以使用 PowerShell 管理虚拟机，无论虚拟机上的网络配置或远程管理设置如何。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="ca9e2-146">可以将 PowerShell Direct 与 JEA 配合使用，向 Hyper-V 管理员提供对 VM 有限的访问权限，这在失去与 VM 的网络连接并需要数据中心管理员来修复网络设置时十分有用。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="ca9e2-147">通过 PowerShell Direct 使用 JEA 无需其他配置，但虚拟机内运行的操作系统必须是 Windows 10 或 Windows Server 2016。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="ca9e2-148">Hyper-V 管理员可以使用 PSRemoting cmdlet 的 `-VMName` 或 `-VMId` 参数连接到 JEA 终结点：</span><span class="sxs-lookup"><span data-stu-id="ca9e2-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="ca9e2-149">强烈建议创建没有其他系统管理权限的本地用户，以供 Hyper-V 管理员使用。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="ca9e2-150">请注意，默认情况下，即使是没有特权的用户，也仍可登录 Windows 计算机（包括使用不受限制的 PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="ca9e2-151">这将使他们能够浏览（某些）文件系统，并深入了解操作系统环境。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="ca9e2-152">若要将 Hyper-V 管理员限制为只能通过将 PowerShell Direct 与 JEA 结合使用来访问 VM，则需要拒绝向 Hyper-V 管理员的 JEA 帐户授予本地登录权限。</span><span class="sxs-lookup"><span data-stu-id="ca9e2-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
