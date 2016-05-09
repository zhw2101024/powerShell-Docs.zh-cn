# 指定跨节点依赖关系

> 适用于：Windows PowerShell 5.0

DSC 提供特殊的资源，**WaitForAll**、**WaitForAny** 和 **WaitForSome**，可用于在配置中指定其他节点上配置的依赖关系。 这些
资源的行为如下所示：

* **WaitForAll**：如果指定的资源在 **NodeName** 属性中定义的所有目标节点上处于所需状态，则该资源成功。
* **WaitForAny**：如果指定的资源在**NodeName** 属性中定义的至少一个目标节点上处于所需状态，则该资源成功。
* **WaitForSome**：指定除 **NodeName** 属性之外的 **NodeCount** 属性。 如果资源在 
 **NodeName** 属性中定义的最小数目的节点（由 **NodeCount**指定）上处于所需状态，则该资源成功。 

## 使用 WaitForXXXX 资源

若要使用 **WaitForXXXX** 资源，可以创建指定要等待的 DSC 资源和节点的该资源类型的资源块。 然后，使用配置中的任何其他资源块内的 **DependsOn** 属性
等待 **WaitForXXXX** 节点指定的条件成功。

例如，在下面的配置中，目标节点正在等待 **xADDomain** 资源 30 秒（以 15 秒为间隔）完成 **MyDC** 节点上的配置， 
之后才可以加入域。

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

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
            Name             = 'MyPC'
            DomainName       = 'Contoso.com'
            Credential       = (get-credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**注意：**默认情况下，WaitForXXX 资源尝试一次，然后就会失败。 虽然这不是必需的，但通常需要指定重试间隔和次数。

## 另请参阅
* [DSC 配置](configurations.md)
* [DSC 资源](resources.md)
* [配置本地配置管理器](metaConfig.md)

<!--HONumber=Apr16_HO4-->


