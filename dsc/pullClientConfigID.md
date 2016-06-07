---
title:   使用配置 ID 设置请求客户端
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 使用配置 ID 设置请求客户端

> 适用于：Windows PowerShell 5.0

必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置的 URL。 若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。 若要配置 LCM，你需要创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。 有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](metaConfig.md)。

> **请注意**：本主题适用于 PowerShell 5.0。 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)

下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。 **ServerURL**

此脚本运行后，将创建名为 **PullClientConfigID** 的新输出文件夹，并在其中放入元配置 MOF 文件。 在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。

若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。 例如： `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## 配置 ID

此脚本将 LCM 的 **ConfigurationID** 属性设置为之前为此目的创建的 GUID（你可以通过使用 **New-Guid** cmdlet 创建 GUID）。 LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。 请求服务器上的配置 MOF 文件必须命名为 _ConfigurationID_.mof，其中 _ConfigurationID_ 是目标节点上 LCM 的 **ConfigurationID** 属性值。

## SMB 请求服务器

若要将客户端设置为从 SMB 服务器请求配置，请使用 **ConfigurationRepositoryShare** 块。 在 **ConfigurationRepositoryShare** 块中，可以通过设置 **SourcePath** 属性指定服务器的路径。 以下元配置将目标节点配置为从名为 **SMBPullServer** 的 SMB 请求服务器请求配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## 资源和报表服务器

如果你在 LCM 配置中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 块（如同上一个示例所示），请求客户端会从指定服务器请求资源，但不会向它发送报表。 虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。 

下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

还可以为资源和报告指定不同的请求服务器。 若要指定资源服务器，请使用 **ResourceRepositoryWeb**（适用于 Web 请求服务器）或 **ResourceRepositoryShare**（适用于 SMB 请求服务器）块。
若要指定报表服务器，请使用 **ReportRepositoryWeb** 块。 报表服务器不能为 SMB 服务器。
以下元配置将请求客户端配置为从 **CONTOSO-PullSrv** 获取其配置、从 **CONTOSO-ResourceSrv** 获取资源、将状态报告发送到 **CONTOSO-ReportSrv**：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## 另请参阅

* [使用配置名称设置请求客户端](pullClientConfigNames.md)



<!--HONumber=May16_HO3-->


