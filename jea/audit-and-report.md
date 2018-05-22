---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 审核和报告
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="auditing-and-reporting-on-jea"></a>JEA 审核和报告

> 适用于：Windows PowerShell 5.0

部署 JEA 后，需要定期审核 JEA 配置。
这可帮助你评估有权访问 JEA 终结点的用户是否正确，以及其分配的角色是否仍适用。

本主题介绍了审核 JEA 终结点的各种方法。

## <a name="find-registered-jea-sessions-on-a-machine"></a>查找计算机上已注册的 JEA 会话

若要查看计算机上注册了哪些 JEA 会话，可使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet。

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

“权限”属性中列出了终结点的有效权限。
这些用户有权连接到 JEA 终结点，但他们有权访问的角色（和命令）却是由注册终结点的[会话配置文件](session-configurations.md)中的“RoleDefinitions”字段决定。

可通过扩展“RoleDefinitions”属性中的数据来评估已注册 JEA 终结点中的角色映射。

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>查找计算机上可用的角色功能

如果角色功能文件存储于有效 PowerShell 模块中的“RoleCapabilities”文件夹中，则仅 JEA 可以使用该文件。
通过搜索可用模块列表，可以查找计算机上可用的所有角色功能。

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> 如果多个角色功能共享同一名称，则此函数的结果顺序无需是选择角色功能的顺序。

## <a name="check-effective-rights-for-a-specific-user"></a>查看特定用户的有效权限

设置 JEA 终结点后，建议检查哪些命令对 JEA 会话中的特定用户适用。
如果某个用户以当前组成员身份启动了一个 JEA 会话，可使用 [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) 枚举适用于该用户的所有命令。
`Get-PSSessionCapability` 的输出与 JEA 会话中运行 `Get-Command -CommandType All` 的指定用户的输出完全相同。

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

如果用户不是将向其授予其他 JEA 权限的组的永久成员，此 cmdlet 可能不会反映这些额外权限。
使用实时 Privileged Access Management 系统允许用户临时隶属于安全组时，通常就是这种情况。
始终仔细评估用户到角色的映射和每个角色的内容，以确保用户仅有权访问成功完成其作业所需的必要命令。

## <a name="powershell-event-logs"></a>PowerShell 事件日志

如果在系统上启用了模块和/或脚本块日志记录，则可以针对每个用户在其 JEA 会话中运行的每条命令，在 Windows 事件日志中查找相应事件。
若要查找这些事件，打开 Windows 事件查看器，导航到“Microsoft-Windows-PowerShell/Operational”事件日志，然后查找事件 ID 为 **4104** 的事件。

每个事件日志条目都将包括在其中运行命令的会话的相关信息。
对于 JEA 会话，这包括有关 **ConnectedUser**即创建 JEA 会话的实际用户和 **RunAsUser**（标识用于执行命令的 JEA 帐户）的重要信息。
应用程序事件日志将显示 RunAsUser 正在进行的更改，因此启用记录或模块/脚本日志记录对跟踪用户的特定命令回调至关重要。

## <a name="application-event-logs"></a>应用程序事件日志

在与外部应用程序或服务交互的 JEA 会话中运行命令时，这些应用程序可能会将事件记录为其自己的事件日志。
与 PowerShell 日志和脚本不同，其他日志记录机制不会捕获 JEA 会话的已连接用户，而只记录虚拟运行身份用户或组托管服务帐户。
若要确定运行该命令的用户，需要参考[会话脚本](#session-transcripts)或相关 PowerShell 事件日志以及在应用程序事件日志中显示的时间和用户。

WinRM 日志还可帮助将应用程序事件日志中的运行身份用户与连接用户相关联。
**Microsoft-Windows-Windows Remote Management/Operational** 日志中 ID 为 **193** 的事件记录了每次创建 JEA 会话时，连接用户和运行身份用户的安全标识符 (SID) 和帐户名称。

## <a name="session-transcripts"></a>会话脚本

如果已将 JEA 配置为为每个用户会话创建脚本，每个用户操作的文本副本将存储在指定的文件夹中。

若要查找所有脚本目录，可在使用 JEA 配置的计算机上以管理员身份运行以下命令：

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

每个脚本的开头部分都包含以下内容：会话开始时间、连接到会话的用户和分配给用户的 JEA 标识。

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

记录的正文记录的是用户调用的每个命令的相关信息。
考虑到针对 PowerShell 远程处理的命令转换方式，用户运行命令的确切语法在 JEA 会话中不适用，但仍可确定已执行的有效命令。
以下示例是来自 JEA 会话中运行 `Get-Service Dns` 的用户的脚本代码段：

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

对于用户运行的每个命令，都将编写“CommandInvocation”行，用于描述用户调用的 cmdlet 或函数。
ParameterBindings 遵循每个 CommandInvocation，介绍使用该命令提供的每个参数和值。
在上述示例中，你可以看到针对“Get-Service”向“Name”参数提供了值“Dns”。

每个命令的输出通常还会对 Out-Default 触发 CommandInvocation。
Out-Default 的 InputObject 是从命令返回的 PowerShell 对象。
该对象的详细信息如下面几行所示，严格模拟用户将看到的内容。

## <a name="see-also"></a>另请参阅

- [审核 JEA 会话中的用户操作](audit-and-report.md)
- [PowerShell ♥ the Blue Team 关于安全的博客文章](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)