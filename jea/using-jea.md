---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: "使用 JEA"
ms.technology: powershell
ms.openlocfilehash: 4f1fad1d28b9ced462c392210449d73af325b132
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
---
# <a name="using-jea"></a>使用 JEA

> 适用于：Windows PowerShell 5.0

本主题介绍连接和使用 JEA 终结点的各种方式。

## <a name="using-jea-interactively"></a>以交互方式使用 JEA

如果你正在测试 JEA 配置或具有需要用户执行的简单任务，可以采用与进行常规 PowerShell 远程处理会话相同的方式使用 JEA。
对于复杂的远程处理任务，建议改为使用[隐式远程处理](#using-jea-with-implicit-remoting)，允许用户在本地处理数据对象，以方便用户进行操作。

以交互方式使用 JEA 需要提供以下信息：
- 要连接到的计算机名称（可以是本地计算机）
- 在该计算机上注册的 JEA 终结点名称
- 该计算机有权访问 JEA 终结点的凭据

获取该信息后，可以使用 [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession) 开始 JEA 会话。

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

如果当前登录的帐户有权访问 JEA 终结点，则可以省略 `-Credential` 参数。

PowerShell 提示更改为 `[localhost]: PS>` 时，你会知道自己正在与远程 JEA 会话交互。
可以运行 `Get-Command` 检查哪些命令可用。
你需要咨询管理员，了解可用参数或允许参数值是否存在任何限制。

提醒一下，由于 JEA 会话在 NoLanguage 模式下运行，因此通常使用 PowerShell 的某些方式可能不适用。
例如，你无法使用变量存储数据或检查从 cmdlet 返回的对象的属性。
下面的示例展示了目前 PowerShell 的使用方式，以及使相同的命令在 NoLanguage 模式下工作的两种方法。

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

对于增加此方法难度的更复杂的命令调用，请考虑使用包含所需功能的[隐式远程处理](#using-jea-with-implicit-remoting)或[创建自定义函数](role-capabilities.md#creating-custom-functions)。

## <a name="using-jea-with-implicit-remoting"></a>将 JEA 与隐式远程处理配合使用

PowerShell 支持备用远程处理模型，在此模型中，用户可以将代理 cmdlet 从远程计算机导入本地计算机，并且可以如同本地命令一样与之交互。
这称为隐式远程处理，[这篇 *Hey, Scripting Guy!*《你好，脚本专家！》博客文章](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)中对此进行了详细介绍。
当隐式远程处理配合 JEA 使用时特别有用，因为它允许在完整语言模式下使用 JEA cmdlet。
这意味着可以使用 Tab 自动补全和变量，操作对象，甚至使用本地脚本对 JEA 终结点更轻松地实现自动化。
每当调用代理命令时，数据将发送到远程计算机上的 JEA 终结点并加以执行。

隐式远程处理工作时，从现有 PowerShell 会话中导入 cmdlet。
可以有选择性地选择使用所选字符串作为每个代理 cmdlet 名词的前缀，以区分哪些命令适用于远程系统。
将创建包含所有代理命令的临时脚本模块，该模块可在本地 PowerShell 会话期间使用。

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> 由于默认 JEA cmdlet 中存在约束，某些系统可能无法导入整个 JEA 会话。
> 为避免这一问题，请向 `-CommandName` 参数显示提供名称，从 JEA 会话仅导入所需的命令。
> 将来的更新会解决在受影响的系统上导入整个 JEA 会话方面的问题。

如果由于默认 JEA 参数存在约束而无法导入 JEA 会话，可以按照以下步骤操作，从导入组中筛选出默认命令。
你仍可使用 `Select-Object` 等命令 - 只需使用安装在计算机上的本地版本，而非 JEA 会话中的远程版本。

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

还可以使用 [Export-pssession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession) 通过隐式远程处理保留代理 cmdlet。
有关隐式远程处理的详细信息，请参阅 [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) 和 [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module) 的帮助文档。

## <a name="using-jea-programatically"></a>以编程方式使用 JEA

JEA 还可用于自动化系统和用户应用程序，例如内部的支持人员应用和 Web 站点。
该方法和生成与非约束 PowerShell 终结点进行会话的应用所用的方法相同，同时警告程序应该注意 JEA 将限制可在远程会话中运行的命令。

对于简单的一次性任务，可以使用 [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) 来运行使用 JEA 的一组命令。

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

若要检查连接到 JEA 会话时哪些命令可用，请运行 `Get-Command` 并循环访问结果以查看允许的参数。

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

如果要生成 C# 应用，可以通过在 [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) 对象中指定配置名称来创建与 JEA 会话连接的 PowerShell 运行空间。

```csharp

// using System.Management.Automation;

var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>将 JEA 与 PowerShell Direct 配合使用

Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession) 功能，即使 VM 位于其他网络中，该功能也可允许 Hyper-V 管理员使用 PowerShell 管理虚拟机。

可以将 PowerShell Direct 与 JEA 配合使用，向 Hyper-V 管理员提供对 VM 有限的访问权限，这在失去与 VM 的网络连接并需要数据中心管理员来修复网络设置时十分有用。

通过 PowerShell Direct 使用 JEA 无需其他配置，但虚拟机内运行的操作系统必须是 Windows 10 或 Windows Server 2016。
Hyper-V 管理员可以使用 PSRemoting cmdlet 的 `-VMName` 或 `-VMId` 参数连接到 JEA 终结点：

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

强烈建议创建没有其他系统管理权限的本地用户，以供 Hyper-V 管理员使用。
请记住，默认情况下，即使没有特权的用户仍可通过使用非约束 PowerShell 等方式登录到 Windows 计算机。
这将使他们能够浏览（某些）文件系统，并深入了解操作系统环境。
若要锁定 Hyper-V 管理员，仅允许将 PowerShell Direct 与 JEA 配合使用来访问 VM，则需要拒绝 Hyper-V 管理员的 JEA 帐户的本地登录权限。