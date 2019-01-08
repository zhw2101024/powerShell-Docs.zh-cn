---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 指定跨节点依赖关系
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400370"
---
# <a name="specifying-cross-node-dependencies"></a>指定跨节点依赖关系

> 适用于：Windows PowerShell 5.0

DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。 这些资源的行为如下所述：

- **WaitForAll**:如果指定的资源是在定义中的所有目标节点上所需状态成功**NodeName**属性。
- **WaitForAny**:如果指定的资源是在至少一个中定义的目标节点上所需状态成功**NodeName**属性。
- **WaitForSome**:指定**NodeCount**属性设置为除**NodeName**属性。 如果资源在 **NodeName** 属性定义的节点（数量下限由 **NodeCount** 指定）上处于所需的状态，则资源成功。

## <a name="syntax"></a>语法

**WaitForAll**并**WaitForAny**资源共享相同的语法。 替换\<ResourceType\>在以下示例中使用**WaitForAny**或**WaitForAll**。
像**DependsOn**关键字，你将需要"[ResourceType] ResourceName"作为名称的格式。 如果资源属于一个单独[配置](configurations.md)，包括**ConfigurationName**带格式字符串中"[ResourceType] ResourceName:: [配置名]:: [配置名]"。 **NodeName**是计算机或节点，应在其等待当前的资源。

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

**WaitForSome**资源具有类似的语法为上述示例中，但将添加**NodeCount**密钥。 **NodeCount**指示当前资源应等待的节点数。

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

所有**WaitForXXXX**共享以下语法项。

| 属性 | 说明 | |RetryIntervalSec |正在重试之前等待的秒数。 最小值为 1。 ||RetryCount |若要重试最大次数。 ||ThrottleLimit |同时连接的计算机数。 默认值是`New-CimSession`默认。 | |DependsOn |指示在配置此资源之前，必须运行其他资源的配置。 有关详细信息，请参阅[DependsOn](resource-depends-on.md)| |PsDscRunAsCredential |请参阅[使用用户凭据使用 DSC](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>使用 WaitForXXXX 资源

每个**WaitForXXXX**资源等待指定的资源，以指定节点上完成。 然后可以通过相同的配置中的其他资源*依赖于* **WaitForXXXX**资源使用**DependsOn**密钥。

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

在编译配置时，将生成两个".mof"文件。 将这两个".mof"文件应用于使用的目标节点[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**注意：** 默认情况下，WaitForXXX 资源尝试一次，然后会失败。 虽然不是必需的您通常最好指定**RetryCount**并**RetryIntervalSec**。

## <a name="see-also"></a>另请参阅

- [DSC 配置](configurations.md)
- [使用资源依赖关系](resource-depends-on.md)
- [DSC 资源](../resources/resources.md)
- [配置本地配置管理器](../managing-nodes/metaConfig.md)
