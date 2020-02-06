---
title: PowerShell Core 6.1 中的新增内容
description: PowerShell Core 6.1 中发布的新功能和更改
ms.date: 09/13/2018
ms.openlocfilehash: 531259217f2b71213776e7d394616c7790e9aca9
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995503"
---
# <a name="whats-new-in-powershell-core-61"></a>PowerShell Core 6.1 中的新增内容

以下是 PowerShell Core 6.1 中引入的一系列新功能和更改。

此外还有使 PowerShell 更快更稳定的“无数”“无聊的东西”（以及很多 bug 修复）  ！ 若要获取更改的完整列表，请查看我们 [GitHub 上的更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。

尽管我们在下面公布了一些名字，但是同样感谢实现此版本的[所有社区参与者](https://github.com/PowerShell/PowerShell/graphs/contributors)。

## <a name="net-core-21"></a>.NET Core 2.1

在[于 5 月发布](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)后，PowerShell Core 6.1 已移动至 .NET Core 2.1，从而对 PowerShell 进行了很多改进，其中包括：

- 性能改进（参见[下方](#performance-improvements)）
- Alpine Linux 支持（预览版）
- [.NET 全局工具支持](/dotnet/core/tools/global-tools) - 即将在 PowerShell 中推出
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>.NET Core 的 Windows 兼容包

在 Windows 上，.NET 团队发布了 [.NET Core 的 Windows 兼容包](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)，这是一组程序集，可将大量已删除的 API 重新添加至 Windows 上的 .NET Core。

我们已将 Windows 兼容包添加到 PowerShell Core 6.1 版本中，让使用这些 API 的任何模块或脚本都能处于可用状态。

Windows兼容包使 PowerShell Core 能使用 Windows 10 2018 年 10 月更新和 Windows Server 2019 附带的 1900 多个 cmdlet  。

## <a name="support-for-application-whitelisting"></a>对应用程序允许列表的支持

PowerShell Core 6.1 与支持 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 和 [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 应用程序允许列表的 Windows PowerShell 5.1 具有奇偶一致性。 根据应用程序允许列表，可使用 PowerShell [受限语言模式](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)精确地控制允许执行的二进制文件。

## <a name="performance-improvements"></a>性能改进

PowerShell Core 6.0 取得了一些显着的性能提升。 PowerShell Core 6.1 持续提高部分操作的速度。

例如，`Group-Object` 的速度提高了 66%：

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| 时间 (秒)   | 25.178                 | 19.653              | 6.641               |
| 加快 (%) | 空值                    | 21.9%               | 66.2%               |

同样，像这样的排序方案提高了 15% 以上：

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| 时间 (秒)   | 12.170                 | 8.493               | 7.08                |
| 加快 (%) | 空值                    | 30.2%               | 16.6%               |

在从 Windows PowerShell 回归后，`Import-Csv` 的速度也显著提升了。
以下示例使用具有 26,616 行和 6 列的测试 CSV：

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| 时间 (秒)   | 0.441                  | 1.069               | 0.268                  |
| 加快 (%) | 空值                    | -142.4%             | 74.9%（来自 WPS 的 39.2%） |

最后，使用 Windows PowerShell，从 JSON 到 `PSObject` 的转换速度提高了 50% 以上。
以下示例使用大约 2MB 的测试 JSON 文件：

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| 时间 (秒)   | 0.259                  | 0.577               | 0.125                  |
| 加快 (%) | 空值                    | -122.8%             | 78.3%（从 WPS 为 51.7%） |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>在 Windows 上检查 `system32` 以获取兼容的内置模块

在 Windows 10 1809 更新和 Windows Server 2019 中，我们更新了许多内置 PowerShell 模块，将其标记为与 PowerShell Core 兼容。

当 PowerShell Core 6.1 启动时，它会自动将 `$windir\System32` 包含为 `PSModulePath` 环境变量的一部分。 但是，如果模块 `CompatiblePSEdition` 被标记为与 `Core` 兼容，则它仅将模块公开给 `Get-Module` 和 `Import-Module`。


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> 可能会看到不同的可用模块，具体取决于安装的角色和功能。

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

可以替代此行为，使用 `-SkipEditionCheck` 开关参数显示所有模块。
我们还在表输出中添加了 `PSEdition` 属性。

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

有关此行为的更多信息，请查看 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)。

## <a name="markdown-cmdlets-and-rendering"></a>Markdown cmdlet 和呈现

Markdown 是创建可读明文文档的标准，其基本格式可以呈现为 HTML。

我们在 6.1 中添加了一些 cmdlet，允许在控制台中转换和呈现 Markdown 文档，包括：

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

例如，`Show-Markdown` 在控制台中呈现 Markdown 文件：

![Show-Markdown 示例](./images/markdown_example.png)

若要详细了解这些 cmdlet 的工作方式，请查看[此 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)。

## <a name="experimental-feature-flags"></a>实验性功能标志

我们启用了对[实验性功能][]的支持。 这允许 PowerShell 开发人员提供新功能，并在设计完成之前获得反馈。 通过这种方式，我们可以避免随着设计的改进而进行重大更改。

使用 `Get-ExperimentalFeature` 获取可用的实验性功能列表。 可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 启用或禁用这些功能。

可以在 [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md) 中了解有关此功能的更多信息。

## <a name="web-cmdlet-improvements"></a>Web cmdlet 的改进

感谢 [@markekraus](https://github.com/markekraus)，我们对 Web cmdlet 进行了一系列改进：[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
和 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod)。

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - 对于 `application-json` 响应，默认编码设置为 UTF-8
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` 参数允许不符合标准的 `Content-Type` 头
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` 参数支持简化的 `multipart/form-data` 支持
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 合规且不区分大小写的关系键处理
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) -添加 Web cmdlet 的 `-Resume` 参数

## <a name="remoting-improvements"></a>远程处理的改进

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>适用于容器的 PowerShell Direct 尝试先使用 PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) 是 PowerShell 和 Hyper-V 的一项功能，允许在没有网络连接或其他远程管理服务的情况下连接到 Hyper-V VM 或容器。

在过去，PowerShell Direct 使用容器上的收件箱 Windows PowerShell 实例进行连接。 现在，PowerShell Direct 先尝试使用 `PATH` 环境变量上任何可用的 `pwsh.exe` 进行连接。 如果 `pwsh.exe` 不可用，PowerShell Direct 则会回退为使用 `powershell.exe`。

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` 现在为预览版本创建单独的远程处理终结点

`Enable-PSRemoting` 现在创建两个远程会话配置：

- 一个用于 PowerShell 的主要版本。 例如，`PowerShell.6` 。 根据“系统范围”的 PowerShell 6 会话配置，次要版本更新可依赖于此终结点
- 一个版本特定的会话配置，例如：`PowerShell.6.1.0`

如果要在同一台计算机上安装并访问多个 PowerShell 6 版本，则此行为会很有帮助。

此外，预览版本的 PowerShell 现在可以在运行 `Enable-PSRemoting` cmdlet 后获取自己的远程会话配置：

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

如果之前未设置 WinRM，则输出可能会有所不同。

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

然后可以查看 PowerShell 6 的预览版和稳定版本以及每个特定版本单独的 PowerShell 会话配置。

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>SSH 支持的 `user@host:port` 语法

SSH 客户端通常支持格式为 `user@host:port` 的连接字符串。 我们通过将 SSH 添加为 PowerShell 远程处理的协议，增加了对这种连接字符串格式的支持：

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>用于在 Windows 上添加资源管理器 shell 上下文菜单的 MSI 选项

感谢 [@bergmeister](https://github.com/bergmeister) 的帮助，现在可以在 Windows 上启用上下文菜单。 现在，可以从 Windows 资源管理器中的任何文件夹打开系统范围的 PowerShell 6.1 安装：

![PowerShell 6 的 Shell 上下文菜单](./images/shell_context_menu.png)

## <a name="goodies"></a>超值服务

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>Windows 快捷方式跳转列表中的“以管理员身份运行”

感谢 [@bergmeister](https://github.com/bergmeister) 的帮助，PowerShell Core 快捷方式的跳转列表现已包含“以管理员身份运行”：

![PowerShell 6 跳转列表中的“以管理员身份运行”](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` 返回到上一目录

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

或者，在 Linux 上：

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

`cd` 和 `cd --` 也更改为 `$HOME`。

### `Test-Connection`

感谢 [@iSazonov](https://github.com/iSazonov) 的帮助，[`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet 已移植到 PowerShell Core。

### <a name="update-help-as-non-admin"></a>`Update-Help` 更改为非管理员命令

根据大众需求，`Update-Help` 不再需要以管理员身份运行。 `Update-Help` 现在默认将帮助保存到用户范围的文件夹。

### <a name="new-methodsproperties-on-pscustomobject"></a>`PSCustomObject` 上的新方法/属性

感谢 [@iSazonov](https://github.com/iSazonov) 的帮助，我们为 `PSCustomObject` 添加了新的方法和属性。 `PSCustomObject` 现在包括类似于其他对象的 `Count`/`Length` 属性。

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

此工作还包括 `ForEach` 和 `Where` 方法，这些方法允许对 `PSCustomObject` 项进行操作和筛选：

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

感谢 @SimonWahlin 的帮助，我们已将 `-Not` 参数添加到 `Where-Object`。 现在可在管道中筛选对象，查看是否有不存在的属性或 null/空属性值。

例如，此命令返回未定义任何依赖服务的所有服务：

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` 创建无 BOM 的 UTF-8 文档

由于我们在 PowerShell 6.0 中推出无 BOM 的 UTF-8，更新了 `New-ModuleManifest` cmdlet 以创建无 BOM 的 UTF-8 文档，而不是 UTF-16 文档。

### <a name="conversions-from-psmethod-to-delegate"></a>从 PSMethod 到委托的转换

感谢 [@powercode](https://github.com/powercode) 的帮助，我们现已支持将 `PSMethod` 转换为委托。 这样，可以执行将 `PSMethod` `[M]::DoubleStrLen` 作为委托值传递到 `[M]::AggregateString` 等操作：

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

有关此更改的详细信息，请参阅 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)。

### <a name="standard-deviation-in-measure-object"></a>`Measure-Object` 中的标准偏差

感谢 [@CloudyDino](https://github.com/CloudyDino) 的帮助，我们已向 `Measure-Object` 添加了 `StandardDeviation` 属性：

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

感谢 [@maybe-hello-world](https://github.com/maybe-hello-world) 的帮助，`Get-PfxCertificate` 现已具备采用 `SecureString` 的 `Password` 参数。 这允许以非交互方式使用它：

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>删除 `more` 函数

在过去，PowerShell 在 Windows 上发布了一个名为 `more` 的函数，它包含 `more.com`。 该函数现在已删除。

此外，`help` 函数已改为在 Windows 上使用 `more.com`，或在非 Windows 平台上使用 `$env:PAGER` 指定的系统默认页导航。

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` 现在将用户返回到该驱动器中的当前工作目录

以前使用 `Set-Location` 或 `cd` 返回到 PSDrive 会将用户发送到该驱动器的默认位置。

感谢 [@mcbobke](https://github.com/mcbobke) 的帮助，现在会将用户发送到该会话最后一个已知的当前工作目录。

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell 类型加速器

我们已在 Windows PowerShell 中包括以下类型加速器，以便更轻松地处理它们对应的类型：

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

这些类型的加速器未包含在 PowerShell 6 中，但已添加到在 Windows 上运行的 PowerShell 6.1 中。

这些类型可用于轻松构建 AD 和 WMI 对象。

例如，可以使用 LDAP 进行查询：

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

以下示例创建 Win32_OperatingSystem CIM 对象：

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

此示例返回 Win32_OperatingSystem 类的 ManagementClass 对象。

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>所有 `-LiteralPath` 参数的 `-lp` 别名

感谢 [@kvprasoon](https://github.com/kvprasoon) 的帮助，我们现在为所有具有 `-LiteralPath` 参数的内置 PowerShell cmdlet 提供了参数别名 `-lp`。

## <a name="breaking-changes"></a>重大更改

### <a name="msi-based-installation-paths-on-windows"></a>Windows 上基于 MSI 的安装路径

在 Windows 上，MSI 包现在会安装到以下路径：

- `$env:ProgramFiles\PowerShell\6\` 用于稳定安装 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` 用于 6.x 的预览安装

此更改确保 Microsoft Update 可以更新/服务于 PowerShell Core。

有关详细信息，请查看 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)。

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>只能使用环境变量禁用遥测

PowerShell Core 在启动时会向 Microsoft 发送基本的遥测数据。 该数据包括 OS 名称、OS 版本和 PowerShell 版本。 此数据帮助我们更好地了解使用 PowerShell 的环境，并能确定新功能和修复的优先级。

要选择退出此遥测，请将环境变量 `POWERSHELL_TELEMETRY_OPTOUT` 设置为 `true`、`yes` 或 `1`。 我们不再支持删除文件 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` 以禁用遥测。

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>在 Unix 平台上的 PowerShell 远程处理中禁用 HTTP 基本身份验证

为了防止使用未加密的流量，Unix 平台上的 PowerShell 远程处理现在需要使用 NTLM/Negotiate 或 HTTPS。

有关这些更改的详细信息，请查看[问题 #6779](https://github.com/PowerShell/PowerShell/issues/6779)。

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>已在 Add-Type 中删除作为受支持语言的 `VisualBasic`

在过去，可以使用 `Add-Type` cmdlet 编译 Visual Basic 代码。 Visual Basic 很少与 `Add-Type` 一起使用。 我们已删除此功能以减小 PowerShell 的大小。

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>已清理 `CommandTypes.Workflow` 和 `WorkflowInfoCleaned` 的使用

有关这些更改的详细信息，请查看 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)。

### <a name="group-object-now-sorts-the-groups"></a>组对象现在对组进行排序

作为性能改进的一部分，`Group-Object` 现在返回组的已排序列表。
虽然不应依赖于顺序，但如果想要第一组，则可能会被此更改所破坏。 我们认为这种性能改进是值得更改的，因为依赖于以前行为的影响很小。

有关此更改的详细信息，请参阅[问题 #7409](https://github.com/PowerShell/PowerShell/issues/7409)。

<!-- URL references -->
[实验性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
