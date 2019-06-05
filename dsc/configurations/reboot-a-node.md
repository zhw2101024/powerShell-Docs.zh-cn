---
ms.date: 01/17/2019
keywords: dsc,powershell,配置,安装程序
title: 重新启动节点
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470742"
---
# <a name="reboot-a-node"></a>重新启动节点

> [!NOTE]
> 本主题讨论如何重新启动节点。 若要使重新启动成功，需要正确配置 ActionAfterReboot  和 RebootNodeIfNeeded  LCM 设置。
> 若要了解本地配置管理器设置，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)或[配置本地配置管理器 (v4)](../managing-nodes/metaConfig4.md)。

可以使用 `$global:DSCMachineStatus` 标志，从资源中重新启动节点。 在 `Set-TargetResource` 函数中将此标志设置为 `1` 会强制 LCM 在当前资源的 Set  方法之后直接重新启动节点。 使用此标志时，xPendingReboot  资源会检测重新启动是否在 DSC 外部挂起。

[配置](configurations.md)可能会执行需要重新启动节点的步骤。 这可能包括诸如以下这类情况：

- Windows 更新
- 安装软件
- 文件重命名
- 计算机重命名

xPendingReboot  资源会检查特定计算机位置，以确定重新启动是否挂起。 如果节点需要在 DSC 外部重新启动，则 xPendingReboot  资源会将 `$global:DSCMachineStatus` 标志设置为 `1`，从而强制重新启动并解决挂起条件。

> [!NOTE]
> 任何 DSC 资源都可以通过在 `Set-TargetResource` 函数中设置此标志，来指示 LCM 重新启动节点。 有关详细信息，请参阅[使用 MOF 编写自定义 DSC 资源](../resources/authoringResourceMOF.md)。

## <a name="syntax"></a>语法

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>“属性”

| 属性 | 说明 |
| --- | --- |
| 名称| 必需参数，对配置中资源的每个实例必须唯一。|
| SkipComponentBasedServicing | 跳过由基于组件的服务组件触发的重新启动。 |
| SkipWindowsUpdate | 跳过由 Windows 更新触发的重新启动。|
| SkipPendingFileRename | 跳过挂起文件重命名重新启动。 |
| SkipCcmClientSDK | 跳过由 ConfigMgr 客户端触发的重新启动。 |
| SkipComputerRename | 跳过由计算机重命名触发的重新启动。 |
| PSDSCRunAsCredential | 在 v5 中受支持。 以指定用户身份执行资源。 |
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 有关详细信息，请参阅[使用 DependsOn](resource-depends-on.md)|

## <a name="example"></a>示例

下面的示例使用 [xExchange](https://github.com/PowerShell/xExchange) 资源安装 Microsoft Exchange。
在整个安装过程中，xPendingReboot  资源用于重新启动节点。

> [!NOTE]
> 此示例需要有权向林中添加 Exchange 服务器的帐户的凭据。 有关在 DSC 中使用凭据的详细信息，请参阅[在 DSC 中处理凭据](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> 此示例假设已将本地配置管理器配置为允许重新启动并在重新启动之后继续配置。

## <a name="where-to-download"></a>下载位置

可以在以下位置或使用 PowerShell 库下载本主题中使用的资源。

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
