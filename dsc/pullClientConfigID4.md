# 在 PowerShell 4.0 中使用配置 ID 设置请求客户端

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置的 URL。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，请创建一个称为“元配置”的特殊配置。 有关配置 LCM 的详细信息，请参阅 [Windows PowerShell 4.0 Desired State Configuration 本地配置管理器](metaConfig4.md)

下面的脚本将 LCM 配置为从名为“PullServer”的服务器请求配置。

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

在该脚本中，**DownloadManagerCustomData** 传递请求服务器的 URL 并（在本示例中）允许不安全的连接。 

此脚本运行后，将创建名为 **SimpleMetaConfigurationForPull** 的新输出文件夹，并在其中放入元配置 MOF 文件。

若要应用配置，请将 **Set-DscLocalConfigurationManager** 用于 **ComputerName**（使用“localhost”）和 **Path**（目标节点的 localhost.meta.mof 文件的位置路径）的参数。 例如： 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## 配置 ID
此脚本将 LCM 的 **ConfigurationID** 属性设置为之前为此目的创建的 GUID（你可以通过使用 **New-Guid** cmdlet 创建 GUID）。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。
<!--HONumber=Feb16_HO4-->
