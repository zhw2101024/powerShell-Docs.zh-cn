---
title: "拉取部分配置命名约定"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##拉取部分配置命名约定
在以前的版本中，部分配置的命名约定为请求服务器/服务中 mof 文件名，应与本地配置管理器设置中指定的部分配置名称匹配，反过来后者必须与 MOF 文件中嵌入的配置名称匹配。 请看下面的快照：- •   本地配置设置，定义了节点可以接收的部分配置。

![示例 metaconfiguration](../../images/MetaConfigPartialOne.png)

•   部分配置定义示例 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   生成的 MOF 文件中嵌入的 ConfigurationName。

![生成的 mof 文件示例](../../images/PartialGeneratedMof.png)

•   拉取配置存储库中的文件名 

![配置存储库中的文件名](../../images/PartialInConfigRepository.png)

Azure 自动化服务名称生成的 mof 文件名为 ``<ConfigurationName>.<NodeName>.mof``。 因此下面的配置将编译为 PartialOne.Localhost.mof。  
这样将无法从 Azure 自动化服务中提取部分配置。

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

在 WMF 5.1 中，请求服务器/服务中的部分配置可以命名为 ``<ConfigurationName>.<NodeName>.mof``。 此外，如果一台计算机从请求服务器/服务中提取一个配置，那么请求服务器配置存储库上的配置文档可以有任何名称。 这种命名灵活性使管理节点的部分配置可通过 onprem 和 Azure Automation 请求服务来实现。 例如，可以有本地进行推送的“基本”部分配置，以及从 Azure Automation 服务进行推送的另一个部分配置。

下面的元配置将设置一个节点，该节点可以在本地管理，也可以由 Azure 自动化服务管理。

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


