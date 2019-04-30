---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 指定跨节点依赖关系
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080197"
---
# <a name="specifying-cross-node-dependencies"></a>指定跨节点依赖关系

> 适用于：Windows PowerShell 5.0

DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。 这些资源的行为如下所述：

- **WaitForAll**：如果指定的资源在 NodeName 属性中定义的所有目标节点上处于所需状态，则该资源成功。
- **WaitForAny**：如果指定的资源在 NodeName 属性中定义的至少一个目标节点上处于所需状态，则该资源成功。
- **WaitForSome**：指定除 NodeName 属性之外的 NodeCount 属性。 如果资源在 **NodeName** 属性定义的节点（数量下限由 **NodeCount** 指定）上处于所需的状态，则资源成功。

## <a name="syntax"></a>语法

WaitForAll 和 WaitForAny 资源共享相同语法。 将以下示例中的 \<ResourceType\> 替换为 WaitForAny 或 WaitForAll。
和 DependsOn 关键字一样，需要将名称的格式设置为“[ResourceType] ResourceName”。 如果资源属于一个单独的[配置](configurations.md)，则在格式化字符串“[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]”中包含 ConfigurationName。 NodeName 是计算机或节点，当前资源应在其中等待。

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

WaitForSome 资源具有与上述示例类似的语法，但添加 NodeCount 项。 NodeCount 指示当前资源应等待的节点数。

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

所有 WaitForXXXX 共享以下语法项。

|  属性  |  说明   | | RetryIntervalSec| 重试之前等待的秒数。 最小值为 1。| | RetryCount| 重试的最大次数。| | ThrottleLimit| 同时连接的计算机数。 默认值默认为 `New-CimSession`。| | DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 有关详细信息，请参阅 [DependsOn](resource-depends-on.md)| |PsDscRunAsCredential | 请参阅[将 DSC 与用户凭据结合使用](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>使用 WaitForXXXX 资源

每个 WaitForXXXX 资源都在指定节点上等待指定资源完成。 然后，相同配置中的其他资源可以使用 DependsOn 项依赖于 WaitForXXXX 资源。

例如，在下面的配置中，目标节点正在等待 **xADDomain** 资源通过最多 30 次重试（时间间隔为 15 秒）在 **MyDC** 节点上完成，然后目标节点才能加入域。

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

在编译配置时，将生成两个“.mof”文件。 使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将这两个“.mof”文件应用于目标节点

>**注意：** 默认情况下，WaitForXXX 资源尝试一次，然后就会失败。 虽然这不是必需的，但通常需要指定 RetryCount 和 RetryIntervalSec。

## <a name="see-also"></a>另请参阅

- [DSC 配置](configurations.md)
- [使用资源依赖项](resource-depends-on.md)
- [DSC 资源](../resources/resources.md)
- [配置本地配置管理器](../managing-nodes/metaConfig.md)
