# 使用新的元配置特性配置 DSC LCM

`DscLocalConfigurationManager` 特性将配置块指定为元配置，用于配置 DSC 本地配置管理器。 此特性将配置限制为仅包含配置 DSC 本地配置管理器的项。 在处理期间，此配置生成 `*.meta.mof` 文件，然后通过使用 `Set-DscLocalConfigurationManager` cmdlet 将其发送到相应的目标节点。

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

以上示例将 LCM 的刷新模式配置为使用请求模式，将配置模式更改为 ApplyAndAutocorrect，并定义请求服务器的类型和位置。

这一新配置特性取代并扩展了 PowerShell 4.0 中 LocalConfigurationManager 资源的功能。 不含此特性的配置中仍支持此 LocalConfigurationManager，以便向后兼容。

元资源：

| **资源名称**            | **说明**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | 用于 DSC 引擎执行的各种设置      |
| PartialConfiguration         | 部分配置设置                 |
| ConfigurationRepositoryWeb   | 基于 Web 的配置存储库             |
| ConfigurationRepositoryShare | 基于文件共享的配置存储库      |
| ResourceRepositoryWeb        | 基于 Web 的资源存储库                  |
| ResourceRepositoryShare      | 基于文件的资源存储库                 |
| ReportServerWeb              | 基于 Web 的请求方案报告端点 |
<!--HONumber=Mar16_HO2-->
