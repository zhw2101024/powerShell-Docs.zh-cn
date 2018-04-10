---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: bd6d61443faf30e4056930a010103e6807c015c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="jea-role-capabilities"></a>JEA 角色功能

> 适用于：Windows PowerShell 5.0

创建 JEA 终结点时，需要定义一个或多个“角色功能”，该功能描述了用户可在 JEA 会话中执行*哪些*操作。
角色功能是一个带 .psrc 扩展名的 PowerShell 数据文件，列出了应向连接用户提供的所有 cmdlet、函数、提供程序和外部程序。

本主题介绍如何为 JEA 用户创建 PowerShell 角色功能文件。

## <a name="determine-which-commands-to-allow"></a>确定要允许的命令

创建角色功能文件时，首先要考虑分配有角色的用户将需要访问哪些内容。
此需求收集过程可能需要一段时间，但非常必要。
如果用户具有访问权限的 cmdlet 和函数太少，则会阻碍他们完成工作。
如果用户可访问的 cmdlet 和函数太多，可能导致其利用隐式管理员权限完成你期望之外的任务，从而降低你的安全性。

此过程的执行方式取决于你的组织和目标，但以下提示有助于确保你符合要求。

1. **标识**用户用于完成工作的命令。 这可能需要调查 IT 员工、检查自动化脚本，或者分析 PowerShell 会话脚本/日志。
2. 将命令行工具**改为**使用 PowerShell 等效工具（若可能），实现最佳的审核和 JEA 自定义体验。 不可将外部程序限制为与本机 PowerShell cmdlet 和 JEA 中的函数一样精细。
3. 必要时，将 cmdlet 的作用域**限制**为仅允许特定参数或参数值。 如果用户应只能管理部分系统，此操作尤其重要。
4. **创建**自定义函数，替换复杂的命令或者很难在 JEA 中进行约束的命令。 封装了复杂命令或应用其他验证逻辑的简单函数可提供额外的掌控力，简化管理员和最终用户的操作。
5. 通过用户和/或自动化服务**测试**允许命令的作用域列表，并根据需要进行调整。

请牢记，通常使用管理员权限（或提升后的权限）运行 JEA 会话中的命令。
有必要仔细选择可用的命令，确保 JEA 终结点不允许连接用户提升其权限。
下面的一些示例介绍了在不受约束的状态下允许使用时可能被恶意使用的命令。
请注意，此列表并非全面详尽，应在开始时谨慎使用。

### <a name="examples-of-potentially-dangerous-commands"></a>可能存在危险的命令示例

风险 | 示例 | 相关命令
-----|---------|-----------------
向连接用户授予管理员特权以绕过 JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`
运行任意代码（如恶意软件、攻击或自定义脚本）以绕过保护 | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`、`New-Service`、`Invoke-Item`、`Invoke-WmiMethod`、`Invoke-CimMethod`、`Invoke-Expression`、`Invoke-Command`、`New-ScheduledTask`、`Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>创建角色功能文件

可使用 [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet 创建新的 PowerShell 角色功能文件。

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

可在文本编辑器中打开生成的角色功能文件，并进行修改以允许角色所需的命令。
PowerShell 帮助文档包括文件配置方式的多个示例。

### <a name="allowing-powershell-cmdlets-and-functions"></a>允许 PowerShell cmdlet 和函数

若要授权用户运行 PowerShell cmdlet 或函数，请将 cmdlet 或函数名称添加到 VisbibleCmdlets 或 VisibleFunctions 字段。
如果不确定命令是 cmdlet 还是函数，可运行 `Get-Command <name>` 并查看输出中的“CommandType”属性。

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

有时，特定 cmdlet 或函数的作用域对用户需求而言过于宽泛。
例如，DNS 管理员可能只需进行访问来重启 DNS 服务。
在租户拥有自助式管理工具的访问权限的多租户环境中，应将租户限制为使用其自己的资源进行管理。
对于这些情况，可限制 cmdlet 或函数中公开的参数。

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

在其他高级应用场景中，可能还需要限制用户能向这些参数提供的值。
通过角色功能，可定义一组允许值，或者定义一种进行提升以确定是否允许给定输入的正则表达式模式。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> 即使限制可用参数，仍始终允许使用[常用 PowerShell 参数](https://technet.microsoft.com/library/hh847884.aspx)。
> 不可在参数字段中明确列出这些参数。

下表介绍自定义可见 cmdlet 或函数的各种方式。
可在 VisibleCmdlets 字段中组合和配对以下任何内容。

示例                                                                                      | 用例
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` 或 `@{ Name = 'My-Func' }`                                                       | 允许用户运行 `My-Func` 且不限制参数。
`'MyModule\My-Func'`                                                                         | 允许用户通过模块 `MyModule` 运行 `My-Func` 且不限制参数。
`'My-*'`                                                                                     | 允许用户使用谓词 `My` 运行任意 cmdlet 或函数。
`'*-Func'`                                                                                   | 允许用户使用名词 `Func` 运行任意 cmdlet 或函数。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | 允许用户使用 `Param1` 和/或 `Param2` 参数运行 `My-Func`。 可向参数提供任何值。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | 允许用户使用 `Param1` 参数运行 `My-Func`。 仅可向该参数提供“Value1”和“Value2”。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | 允许用户使用 `Param1` 参数运行 `My-Func`。 可向参数提供以“contoso”开头的任意值。


> [!WARNING]
> 最佳的安全做法是，建议在定义可见 cmdlet 或函数时不要使用通配符。
> 相反，应明确列出每个受信任的命令，确保共享同一命名方案的其他命令均未在无意中获得授权。

无法向同一个 cmdlet 或函数同时应用 ValidatePattern 和 ValidateSet。

若如此操作，ValidatePattern 将覆盖 ValidateSet。

有关 ValidatePattern 的详细信息，请参阅[*你好，脚本专家*博文](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 正则表达式](https://technet.microsoft.com/library/hh847880.aspx)参考内容。

### <a name="allowing-external-commands-and-powershell-scripts"></a>允许使用外部命令和 PowerShell 脚本

若要允许用户在 JEA 会话中运行可执行文件和 PowerShell 脚本 (.ps1)，必须在 VisibleExternalCommands 字段中添加每个程序的完整路径。

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

如果可能，建议使用你授权的任意外部可执行文件的 PowerShell cmdlet/函数等效项，因为你可控制哪些参数允许使用 PowerShell cmdlet/函数。

很多可执行文件均允许读取当前状态，并允许随后只需提供其他参数即可进行更改。

例如，考虑文件服务器管理员的角色，该管理员想要查看本地计算机托管的网络共享。
一种检查方法是使用 `net share`。
但是，允许 net.exe 会带来很大风险，因为管理员可轻松使用该命令获取 `net group Administrators unprivilegedjeauser /add` 的管理员权限。
更好的方法是允许使用 [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx)，该命令可实现相同的结果，但作用域更受限制。

在 JEA 会话中向用户提供外部命令时，请始终指定可执行文件的完整路径，确保不会转而执行系统其他位置中名称相似（且可能恶意）的程序。

### <a name="allowing-access-to-powershell-providers"></a>允许访问 PowerShell 提供程序

默认情况下，PowerShell 提供程序均不适用于 JEA 会话。

这主要是为了降低向连接用户泄漏敏感信息和配置设置的风险。

必要时，可使用 `VisibleProviders` 命令允许访问 PowerShell 提供程序。
有关提供程序的完整列表，请运行 `Get-PSProvider`。

```powershell
VisibleProviders = 'Registry'
```

对于需要访问文件系统、注册表、证书存储或其他敏感提供程序的简单任务，还可考虑编写将代表用户使用提供程序的自定义函数。
JEA 会话中可用的函数、cmdlet 和外部程序不遵从 JEA 的相同约束；默认情况下，它们可访问任意提供程序。
如果需要将文件复制到 JEA 终结点/从中复制文件，还可考虑使用[用户驱动器](session-configurations.md#user-drive)。

### <a name="creating-custom-functions"></a>创建自定义函数

可在角色功能文件中创作自定义函数，简化最终用户的复杂任务。
如果需要 cmdlet 参数值的高级验证逻辑时，自定义函数也很有用。
可在 **FunctionDefinitions** 字段中编写简单函数：

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> 不要忘记向 **VisibleFunctions** 字段添加自定义函数的名称，使其可由 JEA 用户运行。


自定义函数的主体（脚本块）在系统的默认语言模式下运行，不受 JEA 的语言约束。
这意味着函数可访问文件系统和注册表，并可运行角色功能文件中隐藏的命令。
使用参数时，请注意避免允许运行任意代码，并避免直接将用户输入传输到 `Invoke-Expression` 等 cmdlet 中。

在上例中，可注意到使用的是完全限定的模块名称 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而非速记 `Select-Object`。
角色功能文件中定义的函数仍受限于 JEA 会话的作用域，这包括 JEA 创建用于约束现有命令的代理函数。

Select-Object 是所有 JEA 会话中受约束的默认 cmdlet，不允许选择对象的任意属性。
若要在函数中使用不受约束的 Select-Object，必须通过指定 FQMN 显式请求完整的实现。
JEA 会话中受约束的所有 cmdlet 在通过函数调用时的行为均相同，且符合 PowerShell 的[命令优先顺序](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence)。

如果正在编写大量自定义函数，将其放在 [PowerShell 脚本模块](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx)中可能会更容易。
然后，与使用内置和第三方模块时一样，可使用 VisibleFunctions 字段使这些函数在 JEA 会话中可见。

## <a name="place-role-capabilities-in-a-module"></a>在模块中放置角色功能

为使 PowerShell 能找到角色功能文件，必须将其存储在 PowerShell 模块的“RoleCapabilities”文件夹中。
该模块可存储在 `$env:PSModulePath` 环境变量所内附的任何文件夹中，但不得放置在 System32（针对内置模块保留）或者不受信用户可在其中修改文件的文件夹中。
下例说明了如何在“Program Files”路径中创建名为 *ContosoJEA* 的基本 PowerShell 脚本。

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

若要深入了解 PowerShell 模块、模块清单和 PSModulePath 环境变量，请参阅[了解 PowerShell 模块](https://msdn.microsoft.com/en-us/library/dd878324.aspx)。

## <a name="updating-role-capabilities"></a>更新角色功能


只需保存对角色功能文件的更改，即可随时更新该文件。
角色功能更新后启动的任意新 JEA 会话均可反映出修订后的功能。

这就是有必要控制角色功能文件夹的访问权限的原因。
应该只有高度受信任的管理员才可更改角色功能文件。
如果不受信任的用户可更改角色功能文件，则其可轻松为自己授予 cmdlet 访问权限，便于提升自身权限。


对于想要锁定角色功能访问权限的管理员，请确保本地系统具有角色功能文件的访问权限且包含相关模块。

## <a name="how-role-capabilities-are-merged"></a>如何合并角色功能

用户在输入 JEA 会话时，可获取多个角色功能的访问权限，具体取决于[会话配置文件](session-configurations.md)中的角色映射。
发生此情况时，JEA 将尝试为用户提供所有角色允许的*最宽松*的命令集。

**VisibleCmdlets 和 VisibleFunctions**

最复杂的合并逻辑会影响 cmdlet 和函数，会在 JEA 中限制其参数和参数值。

规则如下：

1. 如果 cmdlet 仅在一个角色中可见，其将会对具有任意适用参数约束的用户可见。
2. 如果 cmdlet 在多个角色中可见，并且每个角色在该 cmdlet 上具有相同的约束，则该 cmdlet 将对具有这些约束的用户可见。
3. 如果 cmdlet 在多个角色中可见，并且每个角色允许使用一组不同的参数，则该 cmdlet 及其在每个角色中定义的所有参数都将对用户可见。 如果角色没有参数约束，则允许使用所有参数。
4. 如果一个角色定义 cmdlet 参数的验证集或验证模式，另一角色允许使用该参数但不约束参数值，则将忽略验证集或验证模式。
5. 如果在多个角色中定义了同一个 cmdlet 参数的验证集，则所有验证集中的所有值均可用。
6. 如果在多个角色中定义了同一个 cmdlet 参数的验证模式，则与任何模式匹配的任何值均可用。
7. 如果在一个或多个角色中定义验证集，在另一角色中定义相同 cmdlet 参数的验证模式，则将忽略应用于剩余验证模式的验证集和规则 (6)。

以下是如何根据这些规则合并角色的示例：

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

角色功能文件中的所有其他字段均简单添加到一组集中且可允许使用的外部命令、别名、提供程序和启动脚本中。
角色功能中可见的任何命令、别名、提供程序或脚本均可供 JEA 用户使用。

请务必确保在包含某角色功能的提供程序和另一角色功能的 cmdlet/函数/命令的组合集中，连接用户不可在无意中访问系统资源。
例如，如果一个角色允许使用 `Remove-Item` cmdlet，而另一角色允许 `FileSystem` 提供程序，则 JEA 用户可能会删除计算机上的任意文件。
有关确定用户有效权限的其他信息，可参阅[审核 JEA 主题](audit-and-report.md)。

## <a name="next-steps"></a>后续步骤

- [创建会话配置文件](session-configurations.md)