---
title: "DSC 模块和配置签名验证"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##DSC 模块和配置签名验证
在 DSC 中，从请求服务器或请求服务器（就 Azure Automation 请求服务来说）将配置文档和模块分发到托管计算机。 如果请求服务器/服务受到攻击，攻击者可能修改请求服务器上的配置和模块，并将其分发到所有托管计算机，从而危及客户的更多计算机。 

 此威胁已在 WMF 5.1 中得到解决。 DSC 支持验证模块和配置文件 (.MOF) 上的数字签名。 该功能可以防止节点执行未经受信任的签名者签署的配置或模块文件，或者是经受信任的签名者签署后被篡改的配置或模块文件。 



###如何对配置和模块进行签名 
***
1. 配置文件 (.MOFS)：- 已扩展现有的 PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 用于支持 MOF 文件签名。  
2. 模块：- 使用以下步骤对相应的模块目录进行签名，从而完成模块签名。 
    * 创建目录文件：目录文件包含加密哈希或指纹的集合。 每个指纹对应于模块中包含的一个文件。  增加了一个新的 cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx)，支持用户为其模块创建目录文件。 请参考目录 cmdlet [相对链接](catalog-cmdlets.md)创建目录文件。 
    * 对目录文件进行签名：使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 对目录文件进行签名。
    * 将目录文件放在模块文件夹中。
按照约定，模块目录文件应放在与模块同名的模块文件夹下面。

###用于启用签名验证的 LocalConfigurationManager 设置。

####请求
节点的 LocalConfigurationManager 根据其当前设置执行模块和配置的签名验证。 默认情况下，签名验证处于禁用状态。 你可以将 SignatureValidation 块添加到节点的元配置定义来启用签名验证，如下所示：-

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

在节点上设置上述元配置可以对下载的配置和模块进行签名验证。 localconfigurationmanager 将执行以下步骤来验证数字签名。
* 验证配置文件 (.MOF) 上的签名是否有效。 它使用在 5.1 中扩展的 powershell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) 来支持 MOF 签名验证。
* 验证授权签名人的证书颁发机构是否可信任。
* 将配置的模块/资源依赖项下载到临时位置。
* 验证模块中是否包含目录的签名。
    * 查找 <moduleName>.cat 文件并使用 cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) 验证其签名。
    * 验证对签名人进行身份验证的证书颁发机构是否可信任。
    * 验证未使用新的 cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) 篡改模块的内容。
* 将模块安装到 $env: ProgramFiles\WindowsPowerShell\Modules\
* 进程配置。

注意：- 仅在第一次将配置应用到系统或下载并安装模块时，才执行对模块目录和配置的签名验证。 一致性运行不会验证 Current.mof 或其模块依赖项的签名。
如果在任何阶段验证失败，例如，如果从请求服务器提取的配置尚未签名，则将终止配置处理，并显示以下错误，以及删除所有临时文件。

![错误输出配置示例](../../images/PullUnsignedConfigFail.PNG)

类似地，提取其目录未签名的模块将导致以下错误：-

![错误输出模块示例](../../images/PullUnisgnedCatalog.PNG)

####推送
通过推送提供的配置可能会在其提供到节点之前在源处被篡改。 本地配置管理器将对推送或发布的配置执行类似的签名验证步骤。
下面是针对推送的签名验证的完整示例。

* 启用针对节点的签名验证。

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* 创建示例配置文件。

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* 尝试将未签名的配置文件推送到节点。 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* 使用代码签名证书对配置文件进行签名。

![SignMofFile](../../images/SignMofFile.PNG)

* 请尝试推送已签名的 mof 文件。

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


