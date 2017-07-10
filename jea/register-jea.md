---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "注册 JEA 配置"
ms.openlocfilehash: 0684a1c7acffbccbedab9dba4689611a24c8ae25
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="registering-jea-configurations" class="xliff"></a>
# 注册 JEA 配置

> 适用于：Windows PowerShell 5.0

创建[角色功能](role-capabilities.md)和[会话配置文件](session-configurations.md)后，最后一步还需注册 JEA 终结点，然后才能使用 JEA。
此过程将会话配置信息应用于系统，并使终结点可供用户和自动化引擎使用。

<a id="single-machine-configuration" class="xliff"></a>
## 单个计算机配置

对于小型环境，可以通过使用 [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 注册会话配置文件来部署 JEA。

在开始之前，请确保已满足以下先决条件：
- 已创建一个或多个角色，并已将其放置于有效 PowerShell 模块的“RoleCapabilities”文件夹中。
- 已创建并测试会话配置文件。
- 注册 JEA 配置的用户在系统上具有管理员权限。

还需选择 JEA 终结点名称。
用户要连接到使用 JEA 的系统时，将需要 JEA 终结点名称。
可使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 查看系统上现有终结点的名称。
Windows 通常随附以“microsoft”开头的终结点。
连接到远程 PowerShell 终结点时，使用的是默认终结点“microsoft.powershell”。

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

如果已确定 JEA 终结点的对应名称，请运行以下命令注册终结点。

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 上述命令将在系统上重启 WinRM 服务。
> 这将终止所有 PowerShell 远程处理会话，以及任何正在进行的 DSC 配置。
> 建议先脱机操作任何生产计算机，然后再运行命令，以避免中断业务操作。

如果注册成功，便可以开始[使用 JEA](using-jea.md)。
可以随时删除会话配置文件；注册后不会再使用它。

<a id="multi-machine-configuration-with-dsc" class="xliff"></a>
## 使用 DSC 的多台计算机配置

如果要在多台计算机上部署 JEA，最简单的部署模型是使用 JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) 资源，在每台计算机上快速且一致地部署 JEA。

若要使用 DSC 部署 JEA，需要确保满足以下先决条件：
- 已创作一个或多个角色功能并已将其添加到有效的 PowerShell 模块。
- 包含角色的 PowerShell 模块存储在每台计算机可访问的（只读）文件共享中。
- 已确定会话配置设置。 使用 JEA DSC 资源时，无需创建会话配置文件。
- 已获得可在每台计算机上执行管理操作的凭据，或有权访问用于管理计算机的 DSC 请求服务器。
- 已下载 [JEA DSC 资源](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

在目标计算机上创建 JEA 终结点的 DSC 配置，如果正在使用请求服务器，也可在请求服务器上操作。
在此配置中，将使用 JustEnoughAdministration DSC 资源来设置会话配置文件和文件资源，以从文件共享通过角色功能进行复制。

下列属性可使用 DSC 资源进行配置：
- 角色定义
- 虚拟帐户组
- 组托管服务帐户名称
- 脚本目录
- 用户驱动器
- 条件访问规则
- JEA 会话的启动脚本

DSC 配置中的每个属性的语法都与 PowerShell 会话配置文件一致。

以下示例是常规服务器维护模块的 DSC 配置。

该示例假定包含“RoleCapabilities”子文件夹中的角色功能的有效 PowerShell 模块位于“\\\\myfileshare\\JEA”文件共享中。


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

随后可在系统上通过[直接调用本地配置管理器](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig)或更新[请求服务器配置](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver)应用此配置。

DSC 资源还可以替换默认的 Microsoft.PowerShell 远程处理终结点。
如果这样做，资源将自动注册包含默认 WinRM ACL（允许远程管理用户和本地管理员组成员访问）且名为“Microsoft.PowerShell.Restricted”的备份非约束终结点。

<a id="unregistering-jea-configurations" class="xliff"></a>
## 注销 JEA 配置

若要删除系统上的 JEA 终结点，请使用 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet。
注销 JEA 终结点将阻止新用户在系统上创建新的 JEA 会话。
它还可以使用相同的终结点名称来重新注册更新后的会话配置文件，从而更新 JEA 配置。

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> 注销 JEA 终结点将导致重启 WinRM 服务。
> 这将中断正在进行的大多数远程管理操作，包括其他 PowerShell 会话、WMI 调用和某些管理工具。
> 请仅在计划的维护时段注销 PowerShell 终结点。

<a id="next-steps" class="xliff"></a>
## 后续步骤

- [测试 JEA 终结点](using-jea.md)

