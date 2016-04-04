# 使用 DSC 报表服务器

> 适用于：Windows PowerShell 5.0

>注意：本主题中描述的报表服务器在 PowerShell 4.0 中不可用。 有关在 PowerShell 4.0 中进行报告的信息，请参阅“使用 DSC 相容服务器”。

可将节点的本地配置管理器 (LCM) 配置为向请求服务器发送有关其配置状态的报表，然后即可查询该服务器以检索此数据。 每当节点检查和应用
配置时，它都会将报表发送到报表服务器。 这些报表存储在服务器上的数据库中，可通过调用报告 Web 服务进行检索。 每个报告中包含
应用的配置、应用配置是否成功、使用的资源、引发的任何错误以及开始和结束时间等信息。

## 将节点配置为发送报表

使用节点上 LCM 配置中的 ReportServerWeb 块告诉节点将报表发送到服务器（有关配置 LCM 的详细信息，
请参阅配置本地配置管理器）。 必须将节点向其发送报表的服务器设置为 Web 请求服务器（不能
将报表发送到 SMB 共享）。 有关设置请求服务器的信息，请参阅设置 DSC 请求服务器。 报表服务器可以是
节点从中请求配置和获取资源的同一服务，也可以是其他服务。
 
在 ReportServerWeb 块中，指定请求服务的 URL 和
服务器已知的注册密钥。
 
以下配置将节点配置为从一项服务请求配置，并将报表发送到
另一台服务器上的服务。 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

以下配置将节点配置为将单个服务器用于配置、资源和报告。

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

>注意：在设置请求服务器时可以将 Web 服务命名为任何所需内容，但是 ServerURL 属性必须与服务名称匹配。

## 获取报表数据

发送到请求服务器的报表将被输入该服务器上的数据库。 通过调用 Web 服务即可使用这些报表。 若要检索特定节点的报表， 
请通过以下形式向报表 Web 服务发送 HTTP 请求：
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
其中 `MyNodeAgentId` 是你想要获取其报表的节点的 AgentId。 可通过在节点上调用 Get-DscLocalConfigurationManager 来
获取该节点的 AgentID。

报表将返回为 JSON 对象数组。

以下脚本将返回其运行于的节点的报表：

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## 查看报表数据

如果将变量设置为 GetReport 函数的结果，就可以查看所返回数组元素中的各个字段：

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

请注意，StatusData 字段是具有以下三个属性的对象：NumberOfResources、Locale 和 ResourcesInDesiredState。 ResourcesInDesiredState
属性是一个对象数组，其中每个对象各有多个属性。 下面的脚本采用单个报表作为参数，循环访问其 ResourcesInDesiredState 数组，
然后将其写入到控制台：
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

以下是调用 GetStatusData 函数后的输出示例：

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

请注意，这些示例旨在让你了解如何使用报表数据。 有关在 PowerShell 中使用 JSON 的介绍，请参阅
Playing with JSON and PowerShell（使用 JSON 和 PowerShell）。

## 另请参阅
>[配置本地配置管理器](metaConfig.md)
>[设置 DSC Web 请求服务器](pullServer.md)
>[使用配置名称设置请求客户端](pullClientConfigNames.md)


<!--HONumber=Mar16_HO4-->


