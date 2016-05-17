---
title:   分离配置和环境数据
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 分离配置和环境数据

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

在 Windows PowerShell Desired State Configuration (DSC) 中，可以从配置的逻辑中分离配置数据。 看待这个问题的另一种思路是把结构配置（例如，配置可能要求安装 IIS）与环境配置分开来看（即无论是测试环境还是生产环境，节点名称都不相同，但两者应用的配置相同）。 这中思路具有以下优势：

* 你可以对不同资源、节点和配置重复使用配置数据。
* 不包含硬编码数据的配置逻辑重用性更高。 这类似于好的函数脚本指南。
* 如果需要更改某些数据，你可以在一个位置进行更改，这样可以节省时间并减少错误。

## 基本概念和示例

DSC 使用 **ConfigurationData** 参数来指定配置的环境部分，此参数是一个哈希表（或者它可以采用包含哈希表的 .psd1 文件）。 此哈希表至少必须具有一个包含结构化值的键 **AllNodes**。 例如：

```powershell
$MyData = 
@{
    AllNodes = @();
    NonNodeData = ""   
}
```

请注意 AllNodes 键的值是一个数组。 此数组的每个元素也是一个需要 NodeName 作为键的哈希表：

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

AllNodes 中的每个哈希表项对应着配置中一个节点的配置数据。 除必需的 NodeName 键之外，你还可以添加其他键到哈希表，例如：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC 提供了三个用于配置脚本的特殊变量：

* **$AllNodes**：指所有节点。 你可以使用带有 **.Where()** 和 **.ForEach()** 的筛选项，这样在上述示例中，你就不必对节点名称进行硬编码来选择操作的特定节点，而可以通过编写类似于以下的内容来选择 VM-1 和 VM-3：

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**：筛选出一组节点后，可以使用 $Node 来指代特定项。 例如：

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

要将属性应用到所有节点，可以设置成 NodeName = “*”。 例如，要让每个节点具有 LogPath 属性，你可以执行如下操作：

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**：你可以在配置内使用此变量来访问作为参数传递的配置数据哈希表。 例如：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

可在 [xWebAdministration 模块](https://powershellgallery.com/packages/xWebAdministration)中查找完整示例。



<!--HONumber=May16_HO3-->


