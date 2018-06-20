---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 分离配置和环境数据
ms.openlocfilehash: 3c7f1ba93b4438b3eb440dc1f2349eff0606ac0a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188116"
---
# <a name="separating-configuration-and-environment-data"></a>分离配置和环境数据

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

通过使用配置数据，可将 DSC 配置中使用的数据与配置本身分离。
这样做可将单个配置用于多个环境。

例如，如果要开发应用程序，可将一个配置同时用于开发和生产环境，并使用配置数据指定每个环境的数据。

## <a name="what-is-configuration-data"></a>什么是配置数据?

配置数据是编译相应配置时在哈希表中定义并传递给 DSC 配置的数据。

有关 **ConfigurationData** 哈希表的详细说明，请参阅[使用配置数据](configData.md)。

## <a name="a-simple-example"></a>一个简单示例

让我们通过一个非常简单的示例来看看其工作方式。
我们将创建单个配置，确保一些节点上存在 **IIS**，另一些节点上存在 **Hyper-V**：

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

此脚本的最后一行将编译配置，将 `$MyData` 作为 **ConfigurationData** 参数的值传递。

结果是将创建两个 MOF 文件：

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` 指定两个不同节点，每个都具有其自己的 `NodeName` 和 `Role`。 配置动态创建“节点”块，方法是采用来自 `$MyData`（特别是 `$AllNodes`）的节点的集合，并根据 `Role` 属性筛选该集合。

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>使用配置数据定义开发环境和生产环境

让我们看一下使用单个配置设置网站的开发和生产环境的完整示例。 在开发环境中，IIS 和 SQL Server 安装在单个节点上。 在生产环境中，IIS 和 SQL Server 安装在不同的节点上。 我们将使用配置数据 .psd1 文件来指定两个不同环境的数据。

 ### <a name="configuration-data-file"></a>配置数据文件

将在名为 `DevProdEnvData.psd1` 的文件中定义开发和生产环境数据，如下所示：

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>配置脚本文件

现在，在配置（在 `.ps1` 文件中定义）中，根据其角色（`MSSQL` 和/或 `Dev`）筛选在 `DevProdEnvData.psd1` 中定义的节点并进行相应配置。
在开发环境中，SQL Server 和 IIS 位于同一个节点上，而在生产环境中，SQL Server 和 IIS 位于两个不同节点上。
站点内容也是不同的，具体由 `SiteContents` 属性指定。

在配置脚本末尾，调用配置（将其编译为 MOF 文档），将 `DevProdEnvData.psd1` 作为 `$ConfigurationData` 参数传递。

>**注意：** 此配置要求在目标节点上安装模块 `xSqlPs` 和 `xWebAdministration`。

让我们在名为 `MyWebApp.ps1` 的文件中定义配置：

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

运行此配置时，将创建三个 MOF 文件（一个用于 **AllNodes** 数组中的每个已命名条目）：

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>使用非节点数据

对于并非节点专用的数据，可以向 **ConfigurationData** 哈希表添加其他键。
以下配置确保了两个网站的存在。
每个网站的数据都在 **AllNodes** 数组中定义。
文件 `Config.xml` 用于这两个网站，因此我们使用名称 `NonNodeData` 在其他键中对该文件进行定义。
请注意，其他键的数量没有限制，并可根据需要对其命名。
`NonNodeData` 不是保留字，它只是我们决定用于命名其他键的名字。

你可以使用特殊变量 **$ConfigurationData** 访问其他键。
在此示例中，通过以下代码行访问 `ConfigFileContents`：
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 在 `File` 资源块中。


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>另请参阅
- [使用配置数据](configData.md)
- [配置数据中的凭据选项](configDataCredentials.md)
- [DSC 配置](configurations.md)
