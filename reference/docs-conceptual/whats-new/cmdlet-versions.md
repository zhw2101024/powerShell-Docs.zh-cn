---
ms.date: 02/03/2020
keywords: powershell, 核心
title: 模块和 cmdlet 发行历史记录
ms.openlocfilehash: 9b7c769198fa2a39d8efcc9602f2a913c041289c
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404981"
---
# <a name="release-history-of-modules-and-cmdlets"></a>模块和 cmdlet 发行历史记录

本文列出了 PowerShell 的各种版本随附的模块和 cmdlet。 这是发行说明中信息的摘要。 如需了解更多详情，请参阅发行说明：

- [PowerShell Core 6.2 的最近更新](what-s-new-in-powershell-core-62.md)
- [PowerShell Core 6.1 的最近更新](what-s-new-in-powershell-core-61.md)
- [PowerShell Core 6.0 的最近更新](what-s-new-in-powershell-core-60.md)
- [PowerShell Core 6.0 的重大变更](breaking-changes-ps6.md)
- [PowerShell Core 6.0 的已知问题](known-issues-ps6.md)

本文正在编写中。 请帮助我们不断更新此信息。

## <a name="module-release-history"></a>模块发行历史记录

|         模块名称/PS 版本          |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlet                                | &check; | &check; | &check; | &check; | 仅限 Windows |
| ISE（在 2.0 中引入）                   | &check; |         |         |         | 仅限 Windows |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | 仅限 Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | 仅限 Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | 仅限 Windows |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | 仅限 Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WsMan.Management                | &check; | &check; | &check; | &check; | 仅限 Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | 仅限 Windows |
| PSReadline 1.x                            | &check; |         |         |         | 仅限 Windows |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | 仅限 Windows |
| PSWorkflow                                | &check; |         |         |         | 仅限 Windows |
| PSWorkflowUtility                         | &check; |         |         |         | 仅限 Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | 可在 PowerShell 5.1 中安装 |

## <a name="cmdlet-release-history"></a>Cmdlet 发行历史记录

### <a name="cimcmdlets"></a>CimCmdlet

|         Cmdlet 名称         |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | 仅限 Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | 仅限 Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | 仅限 Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | 仅限 Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | 仅限 Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | 仅限 Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | 仅限 Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | 仅限 Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | 仅限 Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | 仅限 Windows |

### <a name="ise-introduced-in-20"></a>ISE（在 2.0 中引入）

|    Cmdlet 名称    |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | 仅限 Windows |
| Import-IseSnippet | &check; |      |       |       | 仅限 Windows |
| New-IseSnippet    | &check; |      |       |       | 仅限 Windows |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Cmdlet 名称    |   5.1   |   6.x   |   7.0   |   7.1   | 注意 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Cmdlet 名称            |   5.1   |   6.x   |   7.0   |   7.1   |            注意            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | 仅限 Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | 6\.2 中新增 Linux 支持 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | 6\.2 中新增 Linux 支持 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | 仅限 Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | 6\.2 中新增 Linux 支持 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | 仅限 Windows               |
| Get-Verb                          | &check; |         |         |         | 已移至 Microsoft.PowerShell.Utility 6.0 以上版本 |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | 仅限 Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | 仅限 Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | 仅限 Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | 仅限 Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Cmdlet 名称   |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | 仅限 Windows |
| Get-Counter    | &check; |         | &check; | &check; | 仅限 Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | 仅限 Windows |
| Import-Counter | &check; |         |         |         | 仅限 Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | 仅限 Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Cmdlet 名称    |   5.1   |   6.x   |   7.0   |   7.1   | 注意 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Cmdlet 名称       |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | 仅限 Windows |
| Disable-LocalUser       | &check; |      |       |       | 仅限 Windows |
| Enable-LocalUser        | &check; |      |       |       | 仅限 Windows |
| Get-LocalGroup          | &check; |      |       |       | 仅限 Windows |
| Get-LocalGroupMember    | &check; |      |       |       | 仅限 Windows |
| Get-LocalUser           | &check; |      |       |       | 仅限 Windows |
| New-LocalGroup          | &check; |      |       |       | 仅限 Windows |
| New-LocalUser           | &check; |      |       |       | 仅限 Windows |
| Remove-LocalGroup       | &check; |      |       |       | 仅限 Windows |
| Remove-LocalGroupMember | &check; |      |       |       | 仅限 Windows |
| Remove-LocalUser        | &check; |      |       |       | 仅限 Windows |
| Rename-LocalGroup       | &check; |      |       |       | 仅限 Windows |
| Rename-LocalUser        | &check; |      |       |       | 仅限 Windows |
| Set-LocalGroup          | &check; |      |       |       | 仅限 Windows |
| Set-LocalUser           | &check; |      |       |       | 仅限 Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Cmdlet 名称          |   5.1   |   6.x   |   7.0   |   7.1   |               注意               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | 仅限 Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | 仅限 Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | 仅限 Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | 仅限 Windows                     |
| Complete-Transaction          | &check; |         |         |         | 仅限 Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | 仅限 Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | 仅限 Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | 在 macOS 上不受支持           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | 仅限 Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | 仅限 Windows                     |
| Get-EventLog                  | &check; |         |         |         | 仅限 Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | 仅限 Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | 仅限 Windows                     |
| Get-WmiObject                 | &check; |         |         |         | 仅限 Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | 仅限 Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | 仅限 Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | 仅限 Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | 仅限 Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | 仅限 Windows                     |
| Remove-Computer               | &check; |         |         |         | 仅限 Windows                     |
| Remove-EventLog               | &check; |         |         |         | 仅限 Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | 仅限 Windows                     |
| Remove-WmiObject              | &check; |         |         |         | 仅限 Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | 仅限 Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Restore-Computer              | &check; |         |         |         | 仅限 Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | 仅限 Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | 仅限 Windows                     |
| Show-EventLog                 | &check; |         |         |         | 仅限 Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Start-Transaction             | &check; |         |         |         | 仅限 Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | 7\.0 中新增 Linux/macOS 支持 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | 仅限 Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | 仅限 Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | 仅限 Windows                     |
| Use-Transaction               | &check; |         |         |         | 仅限 Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | 不适用于 Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | 仅限 Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Cmdlet 名称        |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | 仅限 Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Cmdlet 名称         |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | 仅限 Windows |
| Invoke-OperationValidation | &check; |      |       |       | 仅限 Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Cmdlet 名称        |   5.1   |   6.x   |   7.0   |   7.1   |                  注意                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | 在 Linux/macOS 上返回“无限制”  |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | 在 Linux/macOS 上不执行任何操作             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | 仅限 Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | 仅限 Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet 名称        |   5.1   |   6.x   |   7.0   |   7.1   |                   注意                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Linux/macOS 上没有可用的事件源 |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Linux/macOS 上没有可用的事件源 |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | 仅限 Windows                              |
| Out-printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Linux/macOS 上没有可用的事件源 |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Linux/macOS 上没有可用的事件源 |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | 7\.0 中新增 macOS 支持            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Linux/macOS 上没有可用的事件源 |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WsMan.Management

|      Cmdlet 名称       |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | 仅限 Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | 仅限 Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | 仅限 Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | 仅限 Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | 仅限 Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | 仅限 Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | 仅限 Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | 仅限 Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | 仅限 Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | 仅限 Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | 仅限 Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | 仅限 Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Cmdlet 名称        |   5.1   |   6.x   |   7.0   |   7.1   | 注意 |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet 名称           |   5.1   |   6.x   |   7.0   |   7.1   | 注意 |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet 名称                 |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | 仅限 Windows |
| Enable-DscDebug                            | &check; |         |         |         | 仅限 Windows |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | 仅限 Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | 仅限 Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | 仅限 Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | 仅限 Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | 仅限 Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | 仅限 Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | 仅限 Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | 仅限 Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | 仅限 Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | 仅限 Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | 仅限 Windows |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet 名称          |   5.1   |   6.x   |   7.0   |   7.1   |     注意     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | 仅限 Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | 仅限 Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | 仅限 Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | 仅限 Windows |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | 仅限 Windows |

### <a name="psreadline"></a>PSReadline

|         Cmdlet 名称         |   5.1   |   6.x   |   7.0   |   7.1   | 注意 |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet 名称       |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | 仅限 Windows |
| Disable-JobTrigger      | &check; |      |       |       | 仅限 Windows |
| Disable-ScheduledJob    | &check; |      |       |       | 仅限 Windows |
| Enable-JobTrigger       | &check; |      |       |       | 仅限 Windows |
| Enable-ScheduledJob     | &check; |      |       |       | 仅限 Windows |
| Get-JobTrigger          | &check; |      |       |       | 仅限 Windows |
| Get-ScheduledJob        | &check; |      |       |       | 仅限 Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | 仅限 Windows |
| New-JobTrigger          | &check; |      |       |       | 仅限 Windows |
| New-ScheduledJobOption  | &check; |      |       |       | 仅限 Windows |
| Register-ScheduledJob   | &check; |      |       |       | 仅限 Windows |
| Remove-JobTrigger       | &check; |      |       |       | 仅限 Windows |
| Set-JobTrigger          | &check; |      |       |       | 仅限 Windows |
| Set-ScheduledJob        | &check; |      |       |       | 仅限 Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | 仅限 Windows |
| Unregister-ScheduledJob | &check; |      |       |       | 仅限 Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow 和 PSWorkflowUtility

|          Cmdlet 名称          |   5.1   | 6.x  |  7.0  |  7.1  |     注意     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | 仅限 Windows |
| New-PSWorkflowSession         | &check; |      |       |       | 仅限 Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | 仅限 Windows |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet 名称   |  5.1  |   6.x   |   7.0   |   7.1   | 注意 |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | 可在 PowerShell 5.1 中安装 |
