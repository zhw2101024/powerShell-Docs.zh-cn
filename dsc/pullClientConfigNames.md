# 使用配置名称设置请求客户端

> 适用于：Windows PowerShell 5.0

必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置的 URL。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。若要配置 LCM，你需要创建一个使用 DSCLocalConfigurationManager 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅配置本地配置管理器。

> 注意：本主题适用于 PowerShell 5.0。 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅在 PowerShell 4.0 中使用配置 ID 设置请求客户端

下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

在该脚本中，ConfigurationRepositoryWeb 块定义了请求服务器。 ServerURL 属性为请求服务器指定终结点。

RegistrationKey 属性是请求服务器的所有客户端节点与该请求服务器之间的共享密钥。 请求服务器上的文件中存储了相同的值。 ConfigurationNames 属性指定用于客户端节点的配置的名称。 在请求服务器上，必须将此客户端节点的配置 MOF 文件命名为 ConfigurationNames.mof，其中 ConfigurationNames 的值与你在此元配置中设置的 ConfigurationNames 属性的值相匹配。

此脚本运行后，将创建名为 PullClientConfigID 的新输出文件夹，并在其中放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 Set-DscLocalConfigurationManager cmdlet，并将 Path 设置为元配置 MOF 文件的位置。 例如：`Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> 注意：注册密钥仅适用于 Web 请求服务器。 对于 SMB 请求服务器，你仍必须使用 ConfigurationID。 有关使用 ConfigurationID 配置请求服务器的信息，请参阅使用配置 ID 设置请求客户端

## 资源和报表服务器

如果在 LCM 配置中只指定 ConfigurationRepositoryWeb 或 ConfigurationRepositoryShare 块（如同前面的示例），则请求客户端会 
从指定服务器请求资源，但是不会向它发送报表。 可以将单个请求服务器用于配置、资源和报告，但是必须创建 
ReportRepositoryWeb 块以设置报告。 下面的示例演示一个元配置，它将客户端设置为请求配置和资源并将报表数据发送到单个
请求服务器。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```


还可以为资源和报告指定不同的请求服务器。 若要指定资源服务器，请使用 ResourceRepositoryWeb（适用于 Web 请求服务器）或 
ResourceRepositoryShare（适用于 SMB 请求服务器）块。
若要指定报表服务器，请使用 ReportRepositoryWeb 块。 报表服务器不能为 SMB 服务器。
以下元配置将请求客户端配置为从 CONTOSO-PullSrv 获取其配置、从 CONTOSO-ResourceSrv 获取资源、将状态报告发送到 CONTOSO-ReportSrv：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## 另请参阅

* [使用配置 ID 设置请求客户端](pullClientConfigID.md)
* [设置 DSC Web 请求服务器](pullServer.md)


<!--HONumber=Mar16_HO4-->


