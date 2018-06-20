---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: PowerShell Desired State Configuration 部分配置
ms.openlocfilehash: e6d80b065ad9e68517d2952b7643e4c611d82a0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189969"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell Desired State Configuration 部分配置

>适用于：Windows PowerShell 5.0 及更高版本。

在 PowerShell 5.0 中，Desired State Configuration (DSC) 允许从多个源中以片段形式提交配置。 目标节点上的本地配置管理器 (LCM) 将碎片整理到一起，然后将其作为单个配置进行应用。 此功能允许在团队或个人之间共享配置控制权。
例如，如果两个或更多开发人员团队协作提供一项服务，那么每个团队都可以创建配置来管理该服务中由其负责的部分。 可以从不同请求服务器请求其中每个配置，并可以在各个开发阶段加入这些配置。 部分配置还允许不同的个人或团队控制配置节点的不同方面，而无需协调单个配置文档的编辑。 例如，可能由一个团队负责部署 VM 和操作系统，而由另一个团队负责在该 VM 上部署其它应用程序和服务。 使用部分配置，每个团队都可以创建自己的配置，避免任何不必要的复杂配置。

可以在推送模式、请求模式或两种模式的组合下使用部分配置。

## <a name="partial-configurations-in-push-mode"></a>推送模式下的部分配置
若要在推送模式下使用部分配置，你需要在目标节点上配置 LCM 以接收部分配置。 必须使用 Publish-DSCConfiguration cmdlet 将每个部分配置推送到目标。 然后，目标节点将部分配置组合成为单个配置。你可以通过调用 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet 来应用配置。

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>针对推送模式部分配置来配置 LCM
若要针对推送模式下的部分配置来配置 LCM，你可以为每个部分配置创建带有一个 **PartialConfiguration** 块的 **DSCLocalConfigurationManager** 配置。 有关配置 LCM 的详细信息，请参阅 [Windows 配置本地配置管理器](https://technet.microsoft.com/library/mt421188.aspx)。
下面的示例显示了需要两个部分配置的 LCM 配置：一个用于部署操作系统，另一个用于部署和配置 SharePoint。

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

           PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo
```

每个部分配置的 **RefreshMode** 都设置为“Push”。 **PartialConfiguration** 块的名称（在本例中即“ServiceAccountConfig”和“SharePointConfig”）必须与推送到目标节点的配置名称完全匹配。

>**注意：** 每个 **PartialConfiguration** 块的名称都必须与配置脚本中指定的配置实际名称匹配，而不是与 MOF 文件的名称（这应是目标节点的名称或 `localhost`）匹配。

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>发布和启动推送模式部分配置

然后，可以对每个配置调用 [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration)，将包含配置文档的文件夹作为 **Path** 参数进行传递。 `Publish-DSCConfiguration`将配置 MOF 文件放置到目标节点。 发布两个配置后，即可在目标节点上调用 `Start-DSCConfiguration –UseExisting`。

例如，如果你在创作节点上编译了以下配置 MOF 文档：

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

你会发布和运行如下所示的配置：

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**注意：** 运行 [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet 的用户必须在目标节点上拥有管理员权限。

## <a name="partial-configurations-in-pull-mode"></a>请求模式下的部分配置

可以从一个或多个请求服务器请求部分配置（有关请求服务器的详细信息，请参阅 [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)）。 若要执行此操作，必须在要请求部分配置的目标节点上配置 LCM，并在请求服务器上正确命名和定位配置文档。

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>针对请求节点配置来配置 LCM

若要配置 LCM 以从请求服务器请求部分配置，你需要在 **ConfigurationRepositoryWeb**（适用于 HTTP 请求服务器）或者 **ConfigurationRepositoryShare**（适用于 SMB 请求服务器）块上定义请求服务器。 然后创建 **PartialConfiguration** 块，这些块通过使用 **ConfigurationSource** 属性引用请求服务器。 你还需创建**设置**块来指定 LCM 使用请求模式，并指定请求服务器和目标节点用于识别配置的 **ConfigurationNames** 或者 **ConfigurationID**。 下面的元配置定义了名为 CONTOSO-PullSrv 的 HTTP 请求服务器，以及使用该请求服务器的两个部分配置。

有关使用 **ConfigurationNames** 配置 LCM 的详细信息，请参阅[使用配置名称设置请求客户端](pullClientConfigNames.md)。
有关使用 **ConfigurationID** 配置 LCM 的详细信息，请参阅[使用配置 ID 设置请求客户端](pullClientConfigID.md)。

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>使用配置名称针对配置模式配置来配置 LCM

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }

}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>使用配置 ID 针对配置模式配置来配置 LCM

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

你可以从多个请求服务器请求部分配置：定义每个请求服务器，然后在每个 **PartialConfiguration** 块中引用相应请求服务器即可。

创建元配置后，必须运行该元配置以创建配置文档（MOF 文件），然后调用 [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) 以配置 LCM。

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>在请求服务器 (ConfigurationNames) 上命名和放置配置文档

必须将部分配置文档置于请求服务器的 `web.config` 文件中指定为 **ConfigurationPath** 的文件夹中（通常为 `C:\Program Files\WindowsPowerShell\DscService\Configuration`）。

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>在 PowerShell 5.1 中的拉取服务器上命名配置文档

如果只要从单个拉取服务器中拉取一个部分配置，可以对配置文档进行任意命名。
如果要从拉取服务器中拉取多个部分配置，可以将配置文档命名为 `<ConfigurationName>.mof`（其中 _ConfigurationName_ 是部分配置的名称）或 `<ConfigurationName>.<NodeName>.mof`（其中 _ConfigurationName_ 是部分配置的名称，_NodeName_ 是目标节点的名称）。
这样一来，便可以从 Azure Automation DSC 拉取服务器中拉取配置。


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>在 PowerShell 5.0 中的拉取服务器上命名配置文档

配置文档必须按如下所示命名：`ConfigurationName.mof`，其中 _ConfigurationName_ 是部分配置的名称。 在本例中，配置文档应按如下所示命名：

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>在请求服务器 (ConfigurationID) 上命名和放置配置文档

必须将部分配置文档置于请求服务器的 `web.config` 文件中指定为 **ConfigurationPath** 的文件夹中（通常为 `C:\Program Files\WindowsPowerShell\DscService\Configuration`）。 必须将配置文档命名如下：_ConfigurationName_. _ConfigurationID_`.mof`，其中 _ConfigurationName_ 是部分配置的名称，_ConfigurationID_ 是目标节点上 LCM 中定义的配置 ID。 在本例中，配置文档应按如下所示命名：

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>从请求服务器上运行部分配置

在目标节点上配置 LCM，并在请求服务器上正确创建和命名配置文档后，目标节点将请求并合并部分配置，然后按照由 LCM 的 **RefreshFrequencyMins** 属性指定的固定时间间隔应用生成的配置。 如果想要强制进行刷新，则可以调用 [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet 以请求配置，然后调用 `Start-DSCConfiguration –UseExisting` 以应用这些配置。


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>推送与请求混合模式下的部分配置

你还可以混用推送和请求模式以进行部分配置。 也就是说，你可以同时拥有一个从请求服务器请求的部分配置和另一个推送的部分配置。 根据上文各部分所述，指定每个部分配置的刷新模式。
例如，还是以下面的元配置为例，其中 `ServiceAccountConfig` 部分配置处于拉取模式，`SharePointConfig` 部分配置处于推送模式。

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>使用 ConfigurationNames 的推送与请求混合模式

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>使用 ConfigurationID 的推送与请求混合模式

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

请注意，Settings 块中指定的 **RefreshMode** 为“Pull”，而 `SharePointConfig` 部分配置的 **RefreshMode** 为“Push”。

可按照上文所述的相应刷新模式命名和放置配置 MOF 文件。 可调用 **Publish-DSCConfiguration** 来发布 `SharePointConfig` 部分配置，并等待从请求服务器请求 `ServiceAccountConfig` 配置或通过调用 [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx) 强制进行刷新。

## <a name="example-serviceaccountconfig-partial-configuration"></a>ServiceAccountConfig 部分配置示例

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential

        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```
## <a name="example-sharepointconfig-partial-configuration"></a>SharePointConfig 部分配置示例
```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```
##<a name="see-also"></a>另请参阅

**概念**
[Windows PowerShell Desired State Configuration 请求服务器](pullServer.md)

[Windows 配置本地配置管理器](https://technet.microsoft.com/library/mt421188.aspx)