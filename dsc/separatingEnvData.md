---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "分离配置和环境数据"
ms.openlocfilehash: 18b18d805ac248b29526862591df5f0ff785937b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="048c1-103">分离配置和环境数据</span><span class="sxs-lookup"><span data-stu-id="048c1-103">Separating configuration and environment data</span></span>

><span data-ttu-id="048c1-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="048c1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="048c1-105">通过使用配置数据，可将 DSC 配置中使用的数据与配置本身分离。</span><span class="sxs-lookup"><span data-stu-id="048c1-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="048c1-106">这样做可将单个配置用于多个环境。</span><span class="sxs-lookup"><span data-stu-id="048c1-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="048c1-107">例如，如果要开发应用程序，可将一个配置同时用于开发和生产环境，并使用配置数据指定每个环境的数据。</span><span class="sxs-lookup"><span data-stu-id="048c1-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="048c1-108">什么是配置数据?</span><span class="sxs-lookup"><span data-stu-id="048c1-108">What is configuration data?</span></span>

<span data-ttu-id="048c1-109">配置数据是编译相应配置时在哈希表中定义并传递给 DSC 配置的数据。</span><span class="sxs-lookup"><span data-stu-id="048c1-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="048c1-110">有关 **ConfigurationData** 哈希表的详细说明，请参阅[使用配置数据](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="048c1-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="048c1-111">一个简单示例</span><span class="sxs-lookup"><span data-stu-id="048c1-111">A simple example</span></span>

<span data-ttu-id="048c1-112">让我们通过一个非常简单的示例来看看其工作方式。</span><span class="sxs-lookup"><span data-stu-id="048c1-112">Let's look at a very simple example to see how this works.</span></span> <span data-ttu-id="048c1-113">我们将创建单个配置，确保一些节点上存在 **IIS**，另一些节点上存在 **Hyper-V**：</span><span class="sxs-lookup"><span data-stu-id="048c1-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span> 

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

<span data-ttu-id="048c1-114">此脚本的最后一行将编译配置，将 `$MyData` 作为 **ConfigurationData** 参数的值传递。</span><span class="sxs-lookup"><span data-stu-id="048c1-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="048c1-115">结果是将创建两个 MOF 文件：</span><span class="sxs-lookup"><span data-stu-id="048c1-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
<span data-ttu-id="048c1-116">`$MyData` 指定两个不同节点，每个都具有其自己的 `NodeName` 和 `Role`。</span><span class="sxs-lookup"><span data-stu-id="048c1-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="048c1-117">配置动态创建“节点”块，方法是采用来自 `$MyData`（特别是 `$AllNodes`）的节点的集合，并根据 `Role` 属性筛选该集合。</span><span class="sxs-lookup"><span data-stu-id="048c1-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="048c1-118">使用配置数据定义开发环境和生产环境</span><span class="sxs-lookup"><span data-stu-id="048c1-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="048c1-119">让我们看一下使用单个配置设置网站的开发和生产环境的完整示例。</span><span class="sxs-lookup"><span data-stu-id="048c1-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="048c1-120">在开发环境中，IIS 和 SQL Server 安装在单个节点上。</span><span class="sxs-lookup"><span data-stu-id="048c1-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="048c1-121">在生产环境中，IIS 和 SQL Server 安装在不同的节点上。</span><span class="sxs-lookup"><span data-stu-id="048c1-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="048c1-122">我们将使用配置数据 .psd1 文件来指定两个不同环境的数据。</span><span class="sxs-lookup"><span data-stu-id="048c1-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="048c1-123">配置数据文件</span><span class="sxs-lookup"><span data-stu-id="048c1-123">Configuration data file</span></span>

<span data-ttu-id="048c1-124">将在名为 `DevProdEnvData.psd1` 的文件中定义开发和生产环境数据，如下所示：</span><span class="sxs-lookup"><span data-stu-id="048c1-124">We'll define the development and production environment data in a file namd `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="048c1-125">配置脚本文件</span><span class="sxs-lookup"><span data-stu-id="048c1-125">Configuration script file</span></span>

<span data-ttu-id="048c1-126">现在，在配置（在 `.ps1` 文件中定义）中，根据其角色（`MSSQL` 和/或 `Dev`）筛选在 `DevProdEnvData.psd1` 中定义的节点并进行相应配置。</span><span class="sxs-lookup"><span data-stu-id="048c1-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span> <span data-ttu-id="048c1-127">在开发环境中，SQL Server 和 IIS 位于同一个节点上，而在生产环境中，SQL Server 和 IIS 位于两个不同节点上。</span><span class="sxs-lookup"><span data-stu-id="048c1-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span> <span data-ttu-id="048c1-128">站点内容也是不同的，具体由 `SiteContents` 属性指定。</span><span class="sxs-lookup"><span data-stu-id="048c1-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="048c1-129">在配置脚本末尾，调用配置（将其编译为 MOF 文档），将 `DevProdEnvData.psd1` 作为 `$ConfigurationData` 参数传递。</span><span class="sxs-lookup"><span data-stu-id="048c1-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="048c1-130">**注意：**此配置要求在目标节点上安装模块 `xSqlPs` 和 `xWebAdministration`。</span><span class="sxs-lookup"><span data-stu-id="048c1-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="048c1-131">让我们在名为 `MyWebApp.ps1` 的文件中定义配置：</span><span class="sxs-lookup"><span data-stu-id="048c1-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

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

<span data-ttu-id="048c1-132">运行此配置时，将创建三个 MOF 文件（一个用于 **AllNodes** 数组中的每个已命名条目）：</span><span class="sxs-lookup"><span data-stu-id="048c1-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="048c1-133">使用非节点数据</span><span class="sxs-lookup"><span data-stu-id="048c1-133">Using non-node data</span></span>

<span data-ttu-id="048c1-134">对于并非节点专用的数据，可以向 **ConfigurationData** 哈希表添加其他键。</span><span class="sxs-lookup"><span data-stu-id="048c1-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="048c1-135">以下配置确保了两个网站的存在。</span><span class="sxs-lookup"><span data-stu-id="048c1-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="048c1-136">每个网站的数据都在 **AllNodes** 数组中定义。</span><span class="sxs-lookup"><span data-stu-id="048c1-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="048c1-137">文件 `Config.xml` 用于这两个网站，因此我们使用名称 `NonNodeData` 在其他键中对该文件进行定义。</span><span class="sxs-lookup"><span data-stu-id="048c1-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="048c1-138">请注意，其他键的数量没有限制，并可根据需要对其命名。</span><span class="sxs-lookup"><span data-stu-id="048c1-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="048c1-139">`NonNodeData` 不是保留字，它只是我们决定用于命名其他键的名字。</span><span class="sxs-lookup"><span data-stu-id="048c1-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="048c1-140">你可以使用特殊变量 **$ConfigurationData** 访问其他键。</span><span class="sxs-lookup"><span data-stu-id="048c1-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="048c1-141">在此示例中，通过以下代码行访问 `ConfigFileContents`：</span><span class="sxs-lookup"><span data-stu-id="048c1-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="048c1-142">在 `File` 资源块中。</span><span class="sxs-lookup"><span data-stu-id="048c1-142">in the `File` resource block.</span></span>


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


## <a name="see-also"></a><span data-ttu-id="048c1-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="048c1-143">See Also</span></span>
- [<span data-ttu-id="048c1-144">使用配置数据</span><span class="sxs-lookup"><span data-stu-id="048c1-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="048c1-145">配置数据中的凭据选项</span><span class="sxs-lookup"><span data-stu-id="048c1-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="048c1-146">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="048c1-146">DSC Configurations</span></span>](configurations.md)

