---
title: "分离配置和环境数据"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: f8f8ef06cd79af294bad7bb8cf3d6676ab9a69bc
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="separating-configuration-and-environment-data"></a>分离配置和环境数据

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

通过使用内置 DSC **ConfigurationData** 参数，可以定义可在配置中使用的数据。 这样一来，便可创建可用于多个节点或不同环境的单个配置。 例如，如果要开发应用程序，可将一个配置同时用于开发和生产环境，并使用配置数据指定每个环境的数据。

让我们通过一个非常简单的示例来看看其工作方式。 我们将创建单个配置，确保一些节点上存在 **IIS**，另一些节点上存在 **Hyper-V**： 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
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
        }

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

此脚本的最后一行将配置编译成 MOF 文档，将 `$MyData` 作为值 **ConfigurationData** 参数传递。 `$MyData` 指定两个不同节点，每个都具有其自己的 `NodeName` 和 `Role`。 配置动态创建“节点”块，方法是采用来自 `$MyData`（特别是 `$AllNodes`）的节点的集合，并根据 `Role` 属性筛选该集合。

现在让我们更深入详细地看看其工作方式。

## <a name="the-configurationdata-parameter"></a>ConfigurationData 参数

DSC 配置采用了你在编译配置时指定的名为 **ConfigurationData** 的参数。 有关编译配置的信息，请参阅 [DSC 配置](configurations.md)。

**ConfigurationData** 参数是必须具有至少一个名为 **AllNodes** 的键的哈希表。 它也可具有其他键：

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

**AllNodes** 键的值是一个数组。 此数组的每个元素也是必须具有至少一个名为 **NodeName** 的键的哈希表：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

也可以将其他键添加到每个哈希表：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

若要将属性应用到所有节点，可创建 **NodeName** 为 `*` 的 **AllNodes** 数组的成员。 例如，若要让每个节点具有 `LogPath` 属性，可以执行如下操作：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

这相当于添加名称为 `LogPath` 的属性，值 `"C:\Logs"` 添加到其他每个块（`VM-1`、`VM-2` 和 `VM-3`）。

## <a name="defining-the-configurationdata-hashtable"></a>定义 ConfigurationData 哈希表

可将 **ConfigurationData** 定义为作为配置所属的相同脚本文件中的变量（如前例所示），或定义为单独的 .psd1 文件中的变量。 若要在 .psd1 文件中定义 **ConfigurationData**，则创建仅包含表示配置数据的哈希表的文件。

例如，可创建一个名为 `MyData.psd1` 的文件，此文件包含以下内容：

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

若要使用 .psd1 文件中定义的配置数据，可在编译配置时，将该文件的路径和名称作为 **ConfigurationData** 参数的值传递：

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>在配置中使用 ConfigurationData 变量

DSC 提供三种可在配置脚本中使用的特殊变量：**$AllNodes**、**$Node** 和 **$ConfigurationData**。

- **$AllNodes** 指 **ConfigurationData** 中定义的整个节点集合。 可使用 **.Where()** 和 **.ForEach()** 筛选 **AllNodes** 集合。
- **Node** 指使用 **.Where()** 或 **.ForEach()** 筛选 **AllNodes** 集合后，该集合中的特定项。
- **ConfigurationData** 指编译配置时，作为参数传递的整个哈希表。

## <a name="devops-example"></a>DevOps 示例

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
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>配置文件

现在，在配置中，根据角色（`MSSQL` 和/或 `Dev`）筛选在 `DevProdEnvData.psd1` 中定义的节点并进行相应配置。 在开发环境中，SQL Server 和 IIS 位于同一个节点上，而在生产环境中，SQL Server 和 IIS 位于两个不同节点上。 站点内容也是不同的，具体由 `SiteContents` 属性指定。

在配置脚本末尾，调用配置（将其编译为 MOF 文档），将 `DevProdEnvData.psd1` 作为 `$ConfigurationData` 参数传递。

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

   Node $AllNodes.Where($_.Role -contains "Web")
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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>另请参阅
- [配置数据中的凭据选项](configDataCredentials.md)
- [DSC 配置](configurations.md)
