---
title: PowerShell 7 模块兼容性
ms.date: 02/03/2020
ms.openlocfilehash: 02095b8233b6fc7b6d2a30bcb841bfd831a50031
ms.sourcegitcommit: 1fa89ab20d14a61f139f1394c45aaedd5a7c5438
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2020
ms.locfileid: "78935192"
---
# <a name="powershell-7-module-compatibility"></a>PowerShell 7 模块兼容性

本文包含 Microsoft 发布的 PowerShell 模块的列表。 此模块为各种 Microsoft 产品和服务提供管理和支持。 这些模块已更新为本机使用 PowerShell 7，或已针对 PowerShell 7 进行了兼容性测试。 随着更多的模块经过识别和测试，将更新此列表，包含新信息。

如果有要共享的信息或有关于特定模块的问题，请在 [WindowsCompatibility 存储库](https://github.com/PowerShell/WindowsCompatibility)中提出问题。

## <a name="windows-management-modules"></a>Windows 管理模块

Windows 管理模块的安装方式各不相同，具体取决于 Windows 的版本以及为该版本打包模块的方式。

在 Windows Server 上，以管理员身份将功能名称与 [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) cmdlet 一起使用。 例如：

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

在 Windows 10 上，Windows 管理模块作为 Windows 可选功能或 Windows 功能提供   。 必须使用“以管理员身份运行”从提升的会话运行以下命令  。


- 对于 Windows 可选功能

  若要获取可选功能的列表，请运行以下命令：

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  若要安装功能，请执行以下操作：

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  有关详细信息，请参阅：

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- 对于 Windows 功能

  若要获取 Windows 功能的列表，请运行以下命令：

  ```powershell
  Get-WindowsCapability -online
  ```

  请注意，功能包的名称以 `~~~~0.0.1.0` 结尾。 必须使用全名才能安装功能：

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  有关详细信息，请参阅：

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>模块列表

| 模块名称                        | 状态                               | 支持的 OS                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | 本机兼容                  | 具有 RSAT-AD-PowerShell 的 Windows Server 1809+<br>具有 Rsat.ActiveDirectory.DS-LDS.Tools 的 Windows 10 1809+ |
| ADFS                               | 未使用兼容性层进行测试    |                                    |
| AppBackgroundTask                  | 本机兼容                  | Windows 10 1903+                   |
| AppLocker                          | 未使用兼容性层进行测试    |                                    |
| AppvClient                         | 未使用兼容性层进行测试    |                                    |
| Appx                               | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+ |
| AssignedAccess                     | 本机兼容                  | Windows 10 1809+                   |
| BestPractices                      | 未使用兼容性层进行测试    |                                    |
| BitLocker                          | 本机兼容                  | 具有 BitLocker 的 Windows Server 1809+<br>Windows 10 1809+ |
| BitsTransfer                       | 本机兼容                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | 未使用兼容性层进行测试    |                                        |
| BranchCache                        | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+ |
| CimCmdlet                         | 本机兼容                  | 内置于 PowerShell 7 中 |
| ClusterAwareUpdating               | 未使用兼容性层进行测试    |                         |
| ConfigCI                           | 未使用兼容性层进行测试    |                         |
| Defender                           | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+  |
| DeliveryOptimization               | 本机兼容                  | Windows Server 1903+<br>Windows 10 1903+  |
| DFSN                               | 本机兼容                  | 具有 FS-DFS-Namespace 的 Windows Server 1809+<br>具有 Rsat.FailoverCluster.Management.Tools 的 Windows 10 1809+ |
| DFSR                               | 未使用兼容性层进行测试    |                                   |
| DhcpServer                         | 未使用兼容性层进行测试    |                                   |
| DirectAccessClientComponents       | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+  |
| Dism                               | 本机兼容                  | Windows Server 1903+<br>Windows 10 1903+  |
| DnsClient                          | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+  |
| DnsServer                          | 本机兼容                  | 具有 DNS 或 RSAT-DNS-Server 的 Windows Server 1809+<br>具有 Rsat.Dns.Tools 的 Windows 10 1809+ |
| EventTracingManagement             | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+  |
| FailoverClusters                   | 未使用兼容性层进行测试    |                                  |
| FailoverClusterSet                 | 未使用兼容性层进行测试    |                                  |
| FileServerResourceManager          | 本机兼容                  | 具有 FS-Resource-Manager 的 Windows Server 1809+ |
| GroupPolicy                        | 未使用兼容性层进行测试    |                                               |
| HgsClient                          | 本机兼容                  | 具有 Hyper-V 或 RSAT-Shielded-VM-Tools 的 Windows Server 1903+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1903+ |
| HgsDiagnostics                     | 本机兼容                  | 具有 Hyper-V 或 RSAT-Shielded-VM-Tools 的 Windows Server 1809+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1809+ |
| Hyper-V                            | 本机兼容                  | 具有 Hyper-V-PowerShell 的 Windows Server 1809+<br>具有 Microsoft-Hyper-V-Management-PowerShell 的 Windows 10 1809+ |
| IISAdministration                  | 未使用兼容性层进行测试    |                                               |
| 国际                      | 本机兼容                  | Windows Server 1903+<br>Windows 10 1903+      |
| IpamServer                         | 未使用兼容性层进行测试    |                                               |
| iSCSI                              | 未使用兼容性层进行测试    |                                               |
| IscsiTarget                        | 未使用兼容性层进行测试    |                                               |
| ISE                                | 未使用兼容性层进行测试    |                                               |
| Kds                                | 本机兼容                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.PowerShell.Diagnostics   | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.PowerShell.Host          | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.PowerShell.LocalAccounts | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| Microsoft.PowerShell.Management    | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.PowerShell.ODataUtils    | 未使用兼容性层进行测试    |                                               |
| Microsoft.PowerShell.Security      | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.PowerShell.Utility       | 本机兼容                  | 内置于 PowerShell 7 中                       |
| Microsoft.WSMan.Management         | 本机兼容                  | 内置于 PowerShell 7 中                       |
| MMAgent                            | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| MPIO                               | 本机兼容                  | 具有 Multipath-IO 的 Windows Server 1809+        |
| MsDtc                              | 未使用兼容性层进行测试    |                                               |
| NetAdapter                         | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetConnection                      | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetEventPacketCapture              | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLbfo                            | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLldpAgent                       | 未使用兼容性层进行测试    |                                               |
| NetNat                             | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetQos                             | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSecurity                        | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSwitchTeam                      | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetTCPIP                           | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetWNV                             | 未使用兼容性层进行测试    |                                               |
| NetworkConnectivityStatus          | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkController                  | 未使用兼容性层进行测试    |                                               |
| NetworkControllerDiagnostics       | 未使用兼容性层进行测试    |                                               |
| NetworkLoadBalancingClusters       | 未使用兼容性层进行测试    |                                               |
| NetworkSwitchManager               | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkTransition                  | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NFS                                | 本机兼容                  | Windows Server 1809+<br>具有 Rsat.ServerManager.Tools 的 Windows 10 1809+ |
| PackageManagement                  | 本机兼容                  | 内置于 PowerShell 7 中                       |
| PcsvDevice                         | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| PersistentMemory                   | 未使用兼容性层进行测试    |                                               |
| PKI                                | 未使用兼容性层进行测试    |                                               |
| PnpDevice                          | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| PowerShellGet                      | 本机兼容                  | 内置于 PowerShell 7 中                       |
| PrintManagement                    | 本机兼容                  | 具有 Print-Services 的 Windows Server 1903+<br>Windows 10 1903+  |
| ProcessMitigations                 | 本机兼容                  | Windows Server 1903+<br>Windows 10 1903+      |
| 设置                       | 未使用兼容性层进行测试    |                                               |
| PSDesiredStateConfiguration        | 部分                            | 内置于 PowerShell 7 中                       |
| PSDiagnostics                      | 本机兼容                  | 内置于 PowerShell 7 中                       |
| PSScheduledJob                     | 未使用兼容性层 | 内置于 PowerShell 5.1 中                     |
| PSWorkflow                         | 未使用兼容性层进行测试    |                                               |
| PSWorkflowUtility                  | 未使用兼容性层进行测试    |                                               |
| RemoteAccess                       | 未使用兼容性层进行测试    |                                               |
| RemoteDesktop                      | 未使用兼容性层进行测试    |                                               |
| ScheduledTasks                     | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SecureBoot                         | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| ServerCore                         | 未使用兼容性层进行测试    |                                               |
| ServerManager                      | 未使用兼容性层进行测试    |                                               |
| ServerManagerTasks                 | 未使用兼容性层进行测试    |                                               |
| ShieldedVMDataFile                 | 本机兼容                  | 具有 RSAT-Shielded-VM-Tools 的 Windows Server 1903+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1903+ |
| ShieldedVMProvisioning             | 本机兼容                  | 具有 HostGuardian 的 Windows Server 1809+<br>具有 HostGuardian 的 Windows 10 1809+  |
| ShieldedVMTemplate                 | 本机兼容                  | 具有 RSAT-Shielded-VM-Tools 的 Windows Server 1809+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1809+ |
| SmbShare                           | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SmbWitness                         | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SMISConfig                         | 本机兼容                  | 具有 WindowsStorageManagementService 的 Windows Server 1903+ |
| SMS                                | 未使用兼容性层进行测试    |                                               |
| SoftwareInventoryLogging           | 本机兼容                  | Windows Server 1809+                          |
| StartLayout                        | 本机兼容                  | 具有桌面体验的 Windows Server 1809+<br>Windows 10 1809+ |
| 存储                            | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| StorageBusCache                    | 未使用兼容性层进行测试    |                                               |
| StorageMigrationService            | 未使用兼容性层进行测试    |                                               |
| StorageQOS                         | 本机兼容                  | 具有 RSAT-Clustering-PowerShell 的 Windows Server 1809+<br>具有 Rsat.FailoverCluster.Management.Tools 的 Windows 10 1809+ |
| StorageReplica                     | 未使用兼容性层进行测试    |                                               |
| SyncShare                          | 本机兼容                  | 具有 FS-SyncShareService 的 Windows Server 1809+ |
| SystemInsights                     | 未使用兼容性层进行测试    |                                               |
| TLS                                | 未使用兼容性层进行测试    |                                               |
| TroubleshootingPack                | 本机兼容                  | Windows 10 1903+                              |
| TrustedPlatformModule              | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| UEV                                | 本机兼容                  | Windows Server（带桌面体验的服务器的未来版本）<br>Windows 10 1903+ |
| UpdateServices                     | 未使用兼容性层 |                                               |
| VpnClient                          | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| Wdac                               | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| WebAdministration                  | 未使用兼容性层进行测试    |                                               |
| WHEA                               | 本机兼容                  | Windows Server 1903+<br>Windows 10 1903+      |
| WindowsDeveloperLicense            | 本机兼容                  | 具有桌面体验的 Windows Server 1809+<br>Windows 10 1809+ |
| WindowsErrorReporting              | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+      |
| WindowsSearch                      | 本机兼容                  | Windows 10 1903+                              |
| WindowsServerBackup                | 本机兼容                  | 具有 Windows-Server-Backup 的 Windows Server 19H2 |
| WindowsUpdate                      | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+       |
| WindowsUpdateProvider              | 本机兼容                  | Windows Server 1809+<br>Windows 10 1809+       |
