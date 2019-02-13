---
ms.date: 1/17/2019
keywords: dsc,powershell,配置,安装程序
title: 重新启动节点
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676834"
---
# <a name="reboot-a-node"></a>重新启动节点

> [!NOTE]
> 本主题讨论了如何重新启动节点。 为了使重新启动才能成功**ActionAfterReboot**并**RebootNodeIfNeeded** LCM 设置需要正确配置。
> 若要了解有关本地配置管理器设置信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)，或[配置本地配置管理器 (v4)](../managing-nodes/metaConfig4.md)。

节点可以重启从在资源中，通过使用`$global:DSCMachineStatus`标志。 此标志设置为`1`中`Set-TargetResource`函数强制重启后的，直接节点的 LCM**设置**当前资源的方法。 使用此标志**xPendingReboot**资源检测到重新启动处于挂起状态之外 DSC。

你[配置](configurations.md)可能会执行需要重新启动的节点的步骤。 这可能包括以下内容：

- Windows: 更新
- 软件安装
- 重命名文件
- 计算机重命名

**XPendingReboot**资源检查特定计算机位置，以确定重新启动处于挂起状态。 如果节点需要重新启动 DSC，之外**xPendingReboot**资源集`$global:DSCMachineStatus`标记，用于`1`强制重新启动，并且解决挂起的条件。

> [!NOTE]
> 任何 DSC 资源可以指示重启节点中设置此标志的 LCM`Set-TargetResource`函数。 有关详细信息，请参阅[编写自定义 DSC 资源使用 MOF](../resources/authoringResourceMOF.md)。

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
| 名称| 必需的参数，它必须是唯一的资源配置内的每个实例。|
| SkipComponentBasedServicing | 由基于组件的服务组件触发的跳过重新启动。 |
| SkipWindowsUpdate | 由 Windows Update 触发的跳过重新启动。|
| SkipPendingFileRename | 跳过挂起文件重命名的重新启动。 |
| SkipCcmClientSDK | 由 ConfigMgr 客户端触发的跳过重新启动。 |
| SkipComputerRename | 跳过重新进行启动的计算机重命名。 |
| PSDSCRunAsCredential | 在 v5 中受支持。 作为指定的用户执行资源。 |
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 有关详细信息，请参阅[使用 DependsOn](resource-depends-on.md)|

## <a name="example"></a>示例

下面的示例将安装 Microsoft Exchange 使用[xExchange](https://github.com/PowerShell/xExchange)资源。
在安装中，整个**xPendingReboot**资源用于重新启动节点。

> [!NOTE]
> 此示例需要具有权限才能向林中添加 Exchange server 的帐户的凭据。 有关在 DSC 中使用凭据的详细信息，请参阅[在 DSC 中处理凭据](../configurations/configDataCredentials.md)

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
> 此示例假定已配置本地配置管理器，以允许重新启动并继续重新启动后的配置。

## <a name="where-to-download"></a>下载位置

您可以下载本主题的以下位置，或使用 PowerShell 库中使用的资源。

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
