# 指定跨节点依赖关系

通过使用内置 WaitFor\* 资源（WaitForAll、WaitForAny 和 WaitForSome），你现可在配置运行期间指定跨计算机的依赖关系，而无需外部业务流程。 每个 WaitFor\ * 资源的行为如下：

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> 等待指定的资源在 NodeName 属性中定义的<ctype="x-NOTFOUND" mdpre="*" mdpost="*">所有</ctype="x-NOTFOUND">目标节点上处于所需状态。
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> 等待指定的资源在 NodeName 属性中定义的<ctype="x-NOTFOUND" mdpre="*" mdpost="*">任意</ctype="x-NOTFOUND">目标节点上处于所需状态。
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> 等待指定的资源在 NodeName 属性中定义的目标节点中、属性 NodeCount 定义数量的节点上处于所需的状态。

以下资源通过 WS-Man 协议使用 CIM 连接进行节点到节点同步。 通过使用这些资源，一个配置可以等待另一台计算机的特定资源状态更改后再继续执行其自身配置。 

例如，在下面的配置中，目标节点等待 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> 资源在 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> 节点上完成几次重试，然后目标节点才能加入域。

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

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
```
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">提示：</ctype="x-NOTFOUND">默认情况下，WaitFor\* 资源尝试一次然后失败，因此虽然不是必需的，但通常最好指定重试间隔和计数。


<!--HONumber=Mar16_HO3-->


