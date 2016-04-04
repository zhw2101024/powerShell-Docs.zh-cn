# 设置 DSC Web 请求服务器

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

DSC Web 请求服务器是 IIS 中的一项 Web 服务，当目标节点请求 DSC 配置文件时，此服务通过 OData 接口向这些节点提供它们。

使用请求服务器的要求：

* 运行的服务器：
  - WMF/PowerShell 4.0 或更高版本
  - IIS 服务器角色
  - DSC 服务
* 理想情况下，可通过某些方式生成证书，以便保护传递给目标节点上本地配置管理器 (LCM) 的凭据

可使用服务器管理器中的添加角色和功能向导或使用 PowerShell 来添加 IIS 服务器角色和 DSC 服务。 本主题中包含的示例脚本将为你提供这两种方法的步骤。

## 使用 xWebService 资源
设置 Web 请求服务器的最简单方法是使用包含在 xPSDesiredStateConfiguration 模块中的 xWebService 资源。 下列步骤说明如何使用设置 Web 服务的配置中的资源。

1. 调用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) 以安装 **xPSDesiredStateConfiguration** 模块。 **请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。 可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。 
1. 使用 `CERT:\LocalMachine\MY\` 存储空间中的使用者 `"CN=PSDSCPullServerCert"` 创建自签名证书。 可通过 `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"` 命令完成此操作。
1. 在 PowerShell ISE 中，启动 (F5) 以下配置脚本（包含于 **xPSDesiredStateConfiguration** 模块的示例文件夹中，名为 Sample_xDscWebService.ps1）。 此脚本将设置请求服务器和相容服务器。
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. 运行此配置，将你所创建自签名证书的指纹作为 **certificateThumbPrint** 参数进行传递：

```powershell
PS:\>$myCert = Get-ChildItem CERT:\LocalMachine\My | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## 注册密钥
若要允许客户端节点注册到服务器以便使用配置名称代替配置 ID，必须将注册密钥（服务器和客户端节点均已知的 GUID）置于名为 `RegistrationKeys.txt` 的文件中。 默认情况下，由此示例创建的请求服务器需要该文件位于 `C:\Program Files\WindowsPowerShell\DscService` 中。 创建由注册密钥组成的单行文本文件，并将其保存在该文件夹中。
> **注意**：PowerShell 4.0 中不支持注册密钥。 

## 放置配置和资源
请求服务器设置完成后，`$env:PROGRAMFILES\WindowsPowerShell` 之下将出现名为“DscService”的新文件夹。 在该文件夹中，有两个分别名为“Modules”和“Configuration”的文件夹。 在“Modules”文件夹中，放置节点将从此服务器请求的配置所需的任意资源。 在“Configuration”文件夹中，放置将由节点请求的任意配置的配置 MOF 文件。 MOF 文件的名称取决于请求客户端的类型。 以下主题详细描述了如何设置请求客户端：

* [使用配置 ID 设置 DSC 请求客户端](pullClientConfigID.md)
* [使用配置名称设置 DSC 请求客户端](pullClientConfigNames.md)
* [部分配置](partialConfigs.md)

## 创建 MOF 校验和
配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。 若要创建校验和，请调用 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet。 该 cmdlet 将接受 **Path** 参数，该参数指定了配置 MOF 所在的文件夹。 该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。 如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。

校验和文件与配置 MOF 文件必须位于同一目录中（默认为 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`）且具有相同名称（校验文件附加有 `.checksum` 扩展名）。

>**注意**：如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。

## 另请参阅
* [Windows PowerShell Desired State Configuration 概述](overview.md)
* [执行配置](enactingConfigurations.md)
* [如何从 DSC 请求服务器检索节点信息](retrieveNodeInfo.md)


<!--HONumber=Mar16_HO1-->


