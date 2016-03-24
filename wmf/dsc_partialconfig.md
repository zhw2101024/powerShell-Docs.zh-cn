# 使用多个配置片段（部分配置）配置节点

WMF 5.0 可帮助你将配置文档以片段形式传递到节点。 对于要接收配置文档的多个片段的节点，必须将其本地配置管理器 (LCM) 设置为指定预期片段，如本示例中所示。

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

在部分配置中，配置名称必须与 LCM 中定义的名称相匹配。 在上述示例中，应将配置命名为 `OSConfig` 和 `SQLConfig`。

为部分配置设置 LCM 将启用配置协调，但不提供安全功能。<!--HONumber=Mar16_HO2-->
