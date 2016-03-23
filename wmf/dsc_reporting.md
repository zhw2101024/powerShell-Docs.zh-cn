# 向中央位置报告配置状态

可将有关 DSC 配置状态的详细信息发送至运行 DSC 服务的服务器。 Get-DscConfigurationStatus cmdlet 返回的相同信息将发送至 DSC 服务。 通过在元配置中定义报表服务器，可在发生错误或配置成功完成时将此状态发送至服务器。 将节点配置为请求或推送模式后将发送此信息。 状态信息存储在 DSC 服务数据库中。

## 用于报告状态的示例元配置
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
使用公开此状态信息的 DSC 服务创建新的 OData 终结点。 通过将配置 ID 或代理 ID {$guid} 传递给终结点，可以收集和分析节点的所有状态。

## 用于收集配置状态的示例 Web 请求 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
