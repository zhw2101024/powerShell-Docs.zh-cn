# 设置 DSC Web 请求服务器

> 适用于：Windows PowerShell 5.0

DSC Web 请求服务器是 IIS 中的一项 Web 服务，当目标节点请求 DSC 配置文件时，此服务通过 OData 接口向这些节点提供它们。

使用请求服务器的要求：

* 运行的服务器：
  - WMF/PowerShell 5.0 或更高版本
  - IIS 服务器角色
  - DSC 服务
* 理想情况下，可通过某些方式生成证书，以便保护传递给目标节点上本地配置管理器 (LCM) 的凭据

可使用服务器管理器中的添加角色和功能向导或使用 PowerShell 来添加 IIS 服务器角色和 DSC 服务。 本主题中包含的示例脚本将为你提供这两种方法的步骤。

## 使用 xWebService 资源
设置 Web 请求服务器的最简单方法是使用包含在 xPSDesiredStateConfiguration 模块中的 xWebService 资源。 下列步骤说明如何使用设置 Web 服务的配置中的资源。

1. 调用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) 以安装 **xPSDesiredStateConfiguration** 模块。 **请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。 可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。 
1. 从受信任的证书颁发机构（在你的组织或公共颁发机构中）获取 DSC 请求服务器的 SSL 证书。 从颁发机构收到的证书通常采用 PFX 格式。 采用默认位置（应是 CERT:\LocalMachine\My），在将成为请求服务器的节点上安装证书。 记下证书指纹。
1. 选择要用作注册密钥的 GUID。 若要使用 PowerShell 生成一个，请在 PS 提示符处输入以下内容令，然后按 Enter：“``` [guid]::newGuid()```”。 此密钥将由客户端节点用作共享密钥，以便在注册过程中进行身份验证。 有关详细信息，请参阅下面的[注册密钥](#RegKey)部分。
1. 在 PowerShell ISE 中，启动 (F5) 以下配置脚本（包含于 **xPSDesiredStateConfiguration** 模块的示例文件夹中，名为 Sample_xDscWebService.ps1）。 此脚本会设置请求服务器。
  
```powershell
configuration Sample_xDscWebService 
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
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
         } 

        File RegistrationKeyFile
        {
            Ensure          ='Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}

```

1. 运行配置，将 SSL 证书的指纹作为 **certificateThumbPrint** 参数进行传递，并将 GUID 注册密钥作为 **RegistrationKey** 参数进行传递：

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCService -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer
```

## 注册密钥
若要允许客户端节点注册到服务器以便使用配置名称代替配置 ID，需将以上配置创建的注册密钥保存在 `C:\Program Files\WindowsPowerShell\DscService` 中名为 `RegistrationKeys.txt` 的文件中。 注册密钥会在初始注册过程中充当由客户端用于请求服务器的共享密钥。 注册成功完成之后，客户端会生成用于唯一地向请求服务器进行身份验证的自签名证书。 此证书的指纹在本地进行存储，并与请求服务器的 URL 关联。
> **注意**：PowerShell 4.0 中不支持注册密钥。 

为了配置节点以便向请求服务器进行身份验证，注册密钥需要处于将向此请求服务器注册的任何目标节点的元配置中。 请注意，以下元配置中的 **RegistrationKey** 会在目标计算机成功注册之后删除，并且值“140a952b-b9d6-406b-b416-e0f759c9c0e4”必须与请求服务器上的 RegistrationKeys.txt 文件中存储的值匹配。 请始终安全地处理注册密钥值，因为知道它便可以向请求服务器注册任何目标计算机。

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
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL         = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey   = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **注意**：**ReportServerWeb** 部分允许将报表数据发送到请求服务器。 

元配置文件中缺少 **ConfigurationID** 属性暗示请求服务器支持 V2 版本的请求服务器协议，因此需要初始注册。 相反，存在 **ConfigurationID** 意味着使用 V1 版本的请求服务器协议，不会进行注册处理。

>**注意**：在推送方案中，当前版本中存在一个 bug，因此需要在元配置文件中为绝不会向请求服务器注册的节点定义 ConfigurationID 属性。 这会强制使用 V1 请求服务器协议，避免注册失败消息。

## 放置配置和资源
请求服务器设置完成之后，在请求服务器配置中通过 **ConfigurationPath** 和 **ModulePath** 属性定义的文件夹是用于放置可供目标节点请求的模块和配置的位置。 这些文件需要采用特定格式，以便请求服务器可正确处理它们。 

### DSC 资源模块程序包格式
每个资源模块需要进行压缩并按照以下模式 **{模块名称}_{模块版本}.zip** 进行命名。 例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。 每个版本的模块都必须包含在单个 zip 文件中。 由于每个 zip 文件中只有单个版本的资源，因此不支持在 WMF 5.0 中添加的可在单个目录中支持多个模块版本的模块格式。 这意味着在打包 DSC 资源模块以便用于请求服务器之前，需要对目录结构进行少量更改。 WMF 5.0 中包含 DSC 资源的模块的默认格式是“{模块文件夹}\{模块版本}\DscResources\{DSC 资源文件夹}\”。 为请求服务器进行打包之前，只需删除 **{模块版本}** 文件夹，以便路径成为“{模块文件夹}\DscResources\{DSC 资源文件夹}\”。 进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 **ModulePath** 文件夹中。

### 配置 MOF 格式 
配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。 若要创建校验和，请调用 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet。 该 cmdlet 将接受 **Path** 参数，该参数指定了配置 MOF 所在的文件夹。 该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。 如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。 将 MOF 文件及其关联校验和文件置于 **ConfigurationPath** 文件夹中。

>**注意**：如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。

## 工具
为了使请求服务器的设置、验证和管理更加容易，以下工具作为示例包含在最新版本的 xPSDesiredStateConfiguration 模块中：
1. 该模块有助于打包 DSC 资源模块和配置文件以便在请求服务器上使用。 [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). 以下示例：

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. 验证请求服务器是否配置正确的脚本。 [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## 请求客户端配置 
以下主题详细描述了如何设置请求客户端：

* [使用配置 ID 设置 DSC 请求客户端](pullClientConfigID.md)
* [使用配置名称设置 DSC 请求客户端](pullClientConfigNames.md)
* [部分配置](partialConfigs.md)


## 另请参阅
* [Windows PowerShell Desired State Configuration 概述](overview.md)
* [执行配置](enactingConfigurations.md)
* [使用 DSC 报表服务器](reportServer.md)


<!--HONumber=Apr16_HO2-->


