# 使用 Nano Server 上的 DSC

> 适用于：Windows PowerShell 5.0

**Nano Server 上的 DSC** 是 Windows Server 2016 媒体 `NanoServer\Packages` 文件夹中的可选包。 为 Nano Server 创建 VHD 后，可以安装此包。通过
将 **Microsoft-NanoServer-DSC-Package** 指定为 **New-NanoServerImage** 函数的 **Packages** 参数值来创建 VHD。 例如，如果你正在为虚拟机创建 VHD，
命令将如下所示：

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

有关安装和使用 Nano Server，以及如何通过 PowerShell 远程处理管理 Nano Server 的信息，请参阅 
[Nano Server 入门](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## Nano Server 上可用的 DSC 功能

 与完整版的 Windows Server 相比，Nano Server 仅支持有限的 API 集，因此 Nano Server 上的 DSC 暂时没有与在完整 SKU 上运行的 DSC  
 同等的功能。 Nano Server 上的 DSC 正处于积极开发中，且功能尚未完善。
 
 下面的 DSC 功能当前在 Nano Server 上均可用： 


* 推送和请求模式
* 完整版 Windows Server 上存在的所有 DSC cmdlet，包括： 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)
        
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
        
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)

  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
    
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
        
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)

  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)
    
* 编译配置（请参阅 [DSC 配置](configurations.md))
* 编译元配置（请参阅[配置本地配置管理器](metaConfig.md))
* [使用用户凭据运行 DSC (RunAs)](runAsUser.md)
* 基于类的资源（请参阅[使用 PowerShell 类编写自定义 DSC 资源](authoringResourceClass.md))
* [指定跨节点依赖关系](crossNodeDependencies.md) 
* [资源版本控制](sxsResource.md)
* 事件
* 请求客户端（配置和资源）（请参阅[使用配置名称设置请求客户端](pullClientConfigNames.md))
* [部分配置（请求和推送）](partialConfigs.md)
* [向请求服务器报告](reportServer.md) 
* MOF 加密
* 事件日志记录
* Azure 自动化 DSC 报告


* 正常工作的资源
  * [Archive](archiveResource.md)
  * [环境](environmentResource.md)
  * [文件](fileResource.md)
  * [组](groupResource.md)
  * GroupSet
  * [日志](logResource.md)
  * ProcessSet
  * [注册表](registryResource.md)
  * [服务](serviceResource.md)
  * ServiceSet
  * [脚本](scriptResource.md)
  * [用户](userResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)

  * WaitForAll（请参阅[指定跨节点依赖关系](crossNodeDependencies.md))
  * WaitForAny（请参阅[指定跨节点依赖关系](crossNodeDependencies.md))
  * WaitForSome（请参阅[指定跨节点依赖关系](crossNodeDependencies.md))

## Nano Server 上不可用的 DSC 功能

下面的 DSC 功能当前在 Nano 服务器上不可用：

* 请求服务器 - 当前不能在 Nano Server 上设置请求服务器
* 不在功能工作列表中的任何内容

## 在 Nano Server 上使用自定义 DSC 资源
 
由于 Nano Server 上仅可使用的有限的 Windows API 集和 CLR 库，因此在完整 CLR 版的 Windows 上运行的 DSC 资源并不一定适用于 Nano Server。 
在部署任意 DSC 资源到生产环境之前，先完成端到端测试。

## 另请参阅
- [Nano Server 入门](https://technet.microsoft.com/en-us/library/mt126167.aspx)

<!--HONumber=Apr16_HO4-->


