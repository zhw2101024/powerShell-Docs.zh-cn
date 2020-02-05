---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 使用 JEA
ms.openlocfilehash: 912e7a3c46be40ff5b5dfa37fe92b67bab5f98dc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995422"
---
# <a name="using-jea"></a><span data-ttu-id="c0a38-103">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="c0a38-103">Using JEA</span></span>

<span data-ttu-id="c0a38-104">本文介绍连接和使用 JEA 终结点的各种方式。</span><span class="sxs-lookup"><span data-stu-id="c0a38-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="c0a38-105">以交互方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="c0a38-105">Using JEA interactively</span></span>

<span data-ttu-id="c0a38-106">如果你正在测试 JEA 配置或需要用户执行简单任务，可采用与进行常规 PowerShell 远程处理会话相同的方式使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="c0a38-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="c0a38-107">对于复杂的远程处理任务，建议使用[隐式远程处理](#using-jea-with-implicit-remoting)。</span><span class="sxs-lookup"><span data-stu-id="c0a38-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="c0a38-108">通过隐式远程处理，用户可在本地处理数据对象。</span><span class="sxs-lookup"><span data-stu-id="c0a38-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="c0a38-109">若要以交互方式使用 JEA，需要提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="c0a38-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="c0a38-110">要连接到的计算机的名称（可以是本地计算机）</span><span class="sxs-lookup"><span data-stu-id="c0a38-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="c0a38-111">在该计算机上注册的 JEA 终结点名称</span><span class="sxs-lookup"><span data-stu-id="c0a38-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="c0a38-112">在该计算机上有权访问 JEA 终结点的凭据</span><span class="sxs-lookup"><span data-stu-id="c0a38-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="c0a38-113">考虑到该信息，可使用 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 开始 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="c0a38-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="c0a38-114">如果当前用户帐户有权访问 JEA 终结点，则可省略 Credential 参数  。</span><span class="sxs-lookup"><span data-stu-id="c0a38-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="c0a38-115">PowerShell 提示更改为 `[localhost]: PS>` 时，即表示你正在与远程 JEA 会话交互。</span><span class="sxs-lookup"><span data-stu-id="c0a38-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="c0a38-116">可以运行 `Get-Command` 检查哪些命令可用。</span><span class="sxs-lookup"><span data-stu-id="c0a38-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="c0a38-117">咨询管理员，了解可用参数或允许的参数值是否存在任何限制。</span><span class="sxs-lookup"><span data-stu-id="c0a38-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="c0a38-118">请记住，JEA 会话在 NoLanguage 模式下运行。</span><span class="sxs-lookup"><span data-stu-id="c0a38-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="c0a38-119">可能无法使用某些常用的 PowerShell 用法。</span><span class="sxs-lookup"><span data-stu-id="c0a38-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="c0a38-120">例如，无法使用变量来存储数据或检查从 cmdlet 返回的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c0a38-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="c0a38-121">以下示例显示了为在 NoLanguage 模式下工作而获取相同命令的两种方法。</span><span class="sxs-lookup"><span data-stu-id="c0a38-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="c0a38-122">对于让此方法变难的更复杂的命令调用，请考虑使用[隐式远程处理](#using-jea-with-implicit-remoting)或[创建自定义函数](role-capabilities.md#creating-custom-functions)（其中包含所需功能）。</span><span class="sxs-lookup"><span data-stu-id="c0a38-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="c0a38-123">将 JEA 与隐式远程处理配合使用</span><span class="sxs-lookup"><span data-stu-id="c0a38-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="c0a38-124">PowerShell 具有隐式远程处理模型，让你能够从远程计算机导入代理 cmdlet，并如同本地命令一样与之交互。</span><span class="sxs-lookup"><span data-stu-id="c0a38-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="c0a38-125">有关隐式远程处理的解释，请参阅“你好，脚本专家！” </span><span class="sxs-lookup"><span data-stu-id="c0a38-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="c0a38-126">[博客文章](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)。</span><span class="sxs-lookup"><span data-stu-id="c0a38-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="c0a38-127">当隐式远程处理配合 JEA 使用时非常有用，因为它允许在完整语言模式下使用 JEA cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a38-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="c0a38-128">你可使用 Tab 自动补全、变量、操作对象，甚至使用本地脚本对 JEA 终结点自动执行任务。</span><span class="sxs-lookup"><span data-stu-id="c0a38-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="c0a38-129">每次调用代理命令时，数据都会发送到远程计算机上的 JEA 终结点并在此执行。</span><span class="sxs-lookup"><span data-stu-id="c0a38-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="c0a38-130">隐式远程处理工作时，从现有 PowerShell 会话中导入 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a38-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="c0a38-131">可以有选择性地选择使用所选字符串作为每个代理 cmdlet 的名词前缀。</span><span class="sxs-lookup"><span data-stu-id="c0a38-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="c0a38-132">通过前缀，可区分哪些命令适用于远程系统。</span><span class="sxs-lookup"><span data-stu-id="c0a38-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="c0a38-133">系统会创建包含所有代理命令的临时脚本模块，该模块可在本地 PowerShell 会话期间导入。</span><span class="sxs-lookup"><span data-stu-id="c0a38-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="c0a38-134">由于默认 JEA cmdlet 中存在约束，某些系统可能无法导入整个 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="c0a38-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="c0a38-135">为避免这一问题，请向 `-CommandName` 参数显示提供名称，从 JEA 会话仅导入所需的命令。</span><span class="sxs-lookup"><span data-stu-id="c0a38-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="c0a38-136">将来的更新会解决在受影响的系统上导入整个 JEA 会话方面的问题。</span><span class="sxs-lookup"><span data-stu-id="c0a38-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="c0a38-137">如果由于默认参数存在 JEA 约束而无法导入 JEA 会话，请按照以下步骤操作，从导入的集中筛选出默认命令。</span><span class="sxs-lookup"><span data-stu-id="c0a38-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="c0a38-138">你仍可使用 `Select-Object` 等命令，但只能使用安装在计算机上的本地版本，而非从远程 JEA 会话导入的版本。</span><span class="sxs-lookup"><span data-stu-id="c0a38-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="c0a38-139">还可以使用 [Export-pssession](/powershell/microsoft.powershell.utility/Export-PSSession) 通过隐式远程处理保留代理 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a38-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="c0a38-140">有关隐式远程处理的详细信息，请参阅 [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) 和 [Import-Module](/powershell/microsoft.powershell.core/import-module) 的文档。</span><span class="sxs-lookup"><span data-stu-id="c0a38-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="c0a38-141">以编程方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="c0a38-141">Using JEA programmatically</span></span>

<span data-ttu-id="c0a38-142">JEA 还可用于自动化系统和用户应用程序，例如内部的支持人员应用和网站。</span><span class="sxs-lookup"><span data-stu-id="c0a38-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="c0a38-143">方法和构建与不受约束的 PowerShell 终结点进行通信的应用时采用的方法相同。</span><span class="sxs-lookup"><span data-stu-id="c0a38-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="c0a38-144">请确保该程序的设计符合由 JEA 施加的限制。</span><span class="sxs-lookup"><span data-stu-id="c0a38-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="c0a38-145">对于简单的一次性任务，可使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) 在 JEA 会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="c0a38-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="c0a38-146">若要检查连接到 JEA 会话时哪些命令可用，请运行 `Get-Command` 并循环访问结果以查看允许的参数。</span><span class="sxs-lookup"><span data-stu-id="c0a38-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="c0a38-147">要构建 C# 应用，可通过在 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 对象中指定配置名称来创建与 JEA 会话连接的 PowerShell 运行空间。</span><span class="sxs-lookup"><span data-stu-id="c0a38-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="c0a38-148">将 JEA 与 PowerShell Direct 配合使用</span><span class="sxs-lookup"><span data-stu-id="c0a38-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="c0a38-149">Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)；借助此功能，无论虚拟机上的网络配置或远程管理设置如何，Hyper-V 管理员都能使用 PowerShell 管理虚拟机。</span><span class="sxs-lookup"><span data-stu-id="c0a38-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="c0a38-150">可将 PowerShell Direct 与 JEA 结合使用，为 Hyper-V 管理员提供对 VM 的有限访问权限。</span><span class="sxs-lookup"><span data-stu-id="c0a38-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="c0a38-151">如果断开与 VM 的网络连接，并且需要数据中心管理员来修复网络设置，这会非常有用。</span><span class="sxs-lookup"><span data-stu-id="c0a38-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="c0a38-152">无需其他配置即可在 PowerShell Direct 上使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="c0a38-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="c0a38-153">但是，在虚拟机内运行的来宾操作系统必须是 Windows 10、Windows Server 2016 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="c0a38-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="c0a38-154">Hyper-V 管理员可以使用 PSRemoting cmdlet 的 `-VMName` 或 `-VMId` 参数连接到 JEA 终结点：</span><span class="sxs-lookup"><span data-stu-id="c0a38-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="c0a38-155">建议创建具有管理系统所需的最低权限的专用用户帐户，供 Hyper-V 管理员使用。</span><span class="sxs-lookup"><span data-stu-id="c0a38-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="c0a38-156">请记住，默认情况下，即使是没有特权的用户，也可通过使用不受约束的 PowerShell 等方式登录到 Windows 计算机。</span><span class="sxs-lookup"><span data-stu-id="c0a38-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="c0a38-157">这使他们能够浏览文件系统，并深入了解操作系统环境。</span><span class="sxs-lookup"><span data-stu-id="c0a38-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="c0a38-158">若要锁定 Hyper-V 管理员并限制其只能通过结合使用 PowerShell Direct 和 JEA 来访问 VM，则必须拒绝向 Hyper-V 管理员的 JEA 帐户授予本地登录权限。</span><span class="sxs-lookup"><span data-stu-id="c0a38-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
