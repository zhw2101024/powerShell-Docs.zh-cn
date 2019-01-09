---
ms.date: 04/11/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 请求服务
ms.openlocfilehash: 659a8f8b2ce7d34058e789c5de336dc1f1f2abb2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400473"
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration 请求服务

> 适用于：Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

本地配置管理器可由请求服务解决方案集中管理。
使用此方法时，会向服务注册要管理的节点并在 LCM 设置中指定一个配置。
会将配置以及作为配置依赖项所需的全部 DSC 资源下载到计算机，LCM 将使用它们来管理配置。
有关要管理的计算机的状态信息将上传到服务进行报告。
此概念称为“请求服务”。

请求服务的当前选项包括：

- Azure 自动化 Desired State Configuration 服务
- 在 Windows Server 上运行的请求服务
- 由社区维护的开放源解决方案
- SMB 共享

**建议的解决方案**和可用功能最多的选项是 [Azure 自动化 DSC](/azure/automation/automation-dsc-getting-started)。

Azure 服务可以在本地管理私有数据中心或 Azure 和 AWS 等公有云中的节点。
对于服务器无法直接连接到 Internet 的私有环境，请考虑将出站流量限制为仅已发布的 Azure IP 范围（请参阅 [Azure 数据中心 IP 范围](https://www.microsoft.com/en-us/download/details.aspx?id=41653)）。

在 Windows Server 的请求服务上目前暂不可用的在线服务功能包括：
- 所有数据在传输和静止时均处于加密状态
- 自动创建和管理客户端证书
- 用于集中式管理[密码/凭据](/azure/automation/automation-credentials)或[变量](/azure/automation/automation-variables)（例如服务器名称或连接字符串）的机密存储
- 集中式管理节点 [LCM 配置](../managing-nodes/metaConfig.md#basic-settings)
- 将配置集中分配给客户端节点
- 在投入生产之前，将配置更改发布到“Canary 组”用于测试
- 图形报告
  - DSC 资源粒度级别的状态详细信息
  - 客户端计算机中用于故障排除的详细错误消息
- [与 Azure Log Analytics 集成](/azure/automation/automation-dsc-diagnostics)用于警报，与自动化的任务，Android/iOS 应用集成用于报告和警报

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server 中的 DSC 请求服务

可将请求服务配置为在 Windows Server 上运行。
请注意，Windows Server 中包含的请求服务解决方案仅具备存储配置/模块以将报表数据下载并捕获到数据中的功能。
它不具备 Azure 中的服务所提供的许多功能，因此不适合用于评估服务的使用方式。

Windows Server 中提供的请求服务是 IIS 中的一项 Web 服务，当目标节点请求 DSC 配置文件时，此服务通过 OData 接口向这些节点提供它们。

使用请求服务器的要求：

- 运行的服务器：
  - WMF/PowerShell 5.0 或更高版本
  - IIS 服务器角色
  - DSC 服务
- 理想情况下，可通过某些方式生成证书，以便保护传递给目标节点上本地配置管理器 (LCM) 的凭据

将 Windows Server 配置为托管请求服务的最佳方式是使用 DSC 配置。
下面提供了一个示例脚本。

### <a name="supported-database-systems"></a>支持的数据库系统

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT（默认）、MDB |ESENT（默认）、MDB|ESENT（默认）、SQL Server、MDB

从 [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver) 的版本 17090 开始，SQL Server 成为了请求服务（Windows Feature DSC-Service）的支持选项。  这为缩放未迁移至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) 的大型 DSC 环境提供了新选项。

> **注意**：SQL Server 支持不会添加到 WMF 5.1 的以前版本（或更早版本）中，仅在 17090 版本或更高版本的 Windows Server 上提供。

若要将请求服务器配置为使用 SQL Server，可将“SqlProvider”设为 `$true`并将“SqlConnectionString”设为有效的 SQL Server 连接字符串。  有关详细信息，请参阅 [SqlClient 连接字符串](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings)。
若要查看使用 xDscWebService 的 SQL Server 配置的示例，请先阅读[使用 xDscWebService 资源](#using-the-xdscwebservice-resource)，再查看 [GitHub 上的 Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)。

### <a name="using-the-xdscwebservice-resource"></a>使用 xDscWebService 资源

设置 Web 请求服务器的最简单方法是使用包含在 xPSDesiredStateConfiguration 模块中的 xDscWebService 资源。
下列步骤说明如何使用设置 Web 服务的配置中的资源。

1. 调用 [Install-Module](/powershell/module/PowershellGet/Install-Module) 以安装 **xPSDesiredStateConfiguration** 模块。 **注意**：**安装模块**已被纳入**PowerShellGet**模块，后者纳入 PowerShell 5.0。 可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。
1. 从受信任的证书颁发机构（在所在组织或公共颁发机构中）获取 DSC 请求服务器的 SSL 证书。 从颁发机构收到的证书通常采用 PFX 格式。 采用默认位置（应是 CERT:\LocalMachine\My），在将成为请求服务器的节点上安装证书。 记下证书指纹。
1. 选择要用作注册密钥的 GUID。 若要使用 PowerShell 生成一个，请在 PS 提示符处输入以下命令，然后按 Enter：“``` [guid]::newGuid()```”或“```New-Guid```”。 此密钥将由客户端节点用作共享密钥，以便在注册过程中进行身份验证。 有关详细信息，请参阅下面的“注册密钥”部分。
1. 在 PowerShell ISE 中，启动 (F5) 以下配置脚本（包含在 xPSDesiredStateConfiguration 模块的示例文件夹中，名为 Sample_xDscWebServiceRegistration.ps1）。 此脚本会设置请求服务器。

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. 运行配置，将 SSL 证书的指纹作为 **certificateThumbPrint** 参数进行传递，并将 GUID 注册密钥作为 **RegistrationKey** 参数进行传递：

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>注册密钥

若要允许客户端节点注册到服务器以便使用配置名称代替配置 ID，需将以上配置创建的注册密钥保存在 `C:\Program Files\WindowsPowerShell\DscService` 中名为 `RegistrationKeys.txt` 的文件中。 注册密钥会在初始注册过程中充当由客户端用于请求服务器的共享密钥。 注册成功完成之后，客户端会生成用于唯一地向请求服务器进行身份验证的自签名证书。 此证书的指纹在本地进行存储，并与请求服务器的 URL 关联。
> **注意**：在 PowerShell 4.0 中不支持注册密钥。

为了配置节点以便向请求服务器进行身份验证，注册密钥需要处于将向此请求服务器注册的任何目标节点的元配置中。 请注意，以下元配置中的 **RegistrationKey** 会在目标计算机成功注册之后删除，并且值“140a952b-b9d6-406b-b416-e0f759c9c0e4”必须与请求服务器上的 RegistrationKeys.txt 文件中存储的值匹配。 请始终安全地处理注册密钥值，因为知道它便可以向请求服务器注册任何目标计算机。

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> **注意**：**ReportServerWeb**部分允许将报表数据发送到请求服务器。

元配置文件中缺少 **ConfigurationID** 属性暗示请求服务器支持 V2 版本的请求服务器协议，因此需要初始注册。
相反，存在 **ConfigurationID** 意味着使用 V1 版本的请求服务器协议，不会进行注册处理。

>**注意**：在推送方案中，当前版本中存在一个 bug，因此需要在元配置文件中为绝不会向请求服务器注册的节点定义 ConfigurationID 属性。 这会强制使用 V1 请求服务器协议，避免注册失败消息。

## <a name="placing-configurations-and-resources"></a>放置配置和资源

请求服务器设置完成之后，在请求服务器配置中通过 **ConfigurationPath** 和 **ModulePath** 属性定义的文件夹是用于放置可供目标节点请求的模块和配置的位置。
这些文件需要采用特定格式，以便请求服务器可正确处理它们。

### <a name="dsc-resource-module-package-format"></a>DSC 资源模块程序包格式

每个资源模块都需要进行压缩并按照 `{Module Name}_{Module Version}.zip` 模式进行命名。
例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。
每个版本的模块都必须包含在单个 zip 文件中。
由于每个 zip 文件中只有单个版本的资源，因此不支持在 WMF 5.0 中添加的可在单个目录中支持多个模块版本的模块格式。
这意味着在打包 DSC 资源模块以便用于请求服务器之前，需要对目录结构进行少量更改。
WMF 5.0 中包含 DSC 资源的模块默认格式是 {Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'。
为请求服务器进行打包之前，删除 {Module version} 文件夹，让路径变为 {Module Folder}\DscResources\{DSC Resource Folder}\'。
进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 **ModulePath** 文件夹中。

使用 `New-DscChecksum {module zip file}` 可为新添加的模块创建校验和文件。

### <a name="configuration-mof-format"></a>配置 MOF 格式

配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。
若要创建校验和，请调用 [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet。
该 cmdlet 将接受 **Path** 参数，该参数指定了配置 MOF 所在的文件夹。
该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。
如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。
将 MOF 文件及其关联校验和文件置于 ConfigurationPath 文件夹中。

>**注意**：如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。

### <a name="tooling"></a>工具

为了使请求服务器的设置、验证和管理更加容易，以下工具作为示例包含在最新版本的 xPSDesiredStateConfiguration 模块中：

1. 该模块有助于打包 DSC 资源模块和配置文件以便在请求服务器上使用。 [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). 以下示例：

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. 验证请求服务器是否配置正确的脚本。 [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>请求服务的社区解决方案

DSC 社区已创作多个解决方案来实现请求服务协议。
对于本地环境，这些解决方案使请求服务具有相关功能，使之有机会以渐进式增强方式回馈社区。

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>请求客户端配置

以下主题详细描述了如何设置请求客户端：

- [设置 DSC 请求客户端使用配置 ID](pullClientConfigID.md)
- [设置 DSC 请求客户端使用配置名称](pullClientConfigNames.md)
- [部分配置](partialConfigs.md)

## <a name="see-also"></a>另请参阅

- [Windows PowerShell Desired State Configuration 概述](../overview/overview.md)
- [执行配置](enactingConfigurations.md)
- [使用 DSC 报表服务器](reportServer.md)
- [[MS-DSCPM]:Desired State Configuration 请求模型协议](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]:Desired State Configuration 请求模型协议 Errata](https://msdn.microsoft.com/library/mt612824.aspx)
