---
title:   DSC 配置
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC 配置

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

DSC 配置是定义某一特殊类型函数的 PowerShell 脚本。 
若要定义配置，你可使用 PowerShell 关键字 __Configuration__。

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

将脚本保存为 .ps1 文件。

## 配置语法

配置脚本由以下部分组成：

- **配置**块。 这是最外层的脚本块。 你可通过使用 **Configuration** 关键字并提供配置名进行定义。 在这种情况下，该配置名为“MyDscConfiguration”。
- 一个或多个**节点**块。 这些将定义正在配置的节点（计算机或 VM）。 在以上配置中，有一个以计算机为目标的名为“TEST-PC1”的**节点**块。
- 一个或多个资源块。 这是此配置为其正在配置的资源设置属性的位置。 在这种情况下，有两个资源块，每个资源块都调用“WindowsFeature”资源。

在**配置**块中，你可以执行通常可在 PoweShell 函数中执行的任何操作。 例如，在上一示例中，如果不想在配置中对目标计算机名进行硬编码，则可以为节点名添加参数：

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

在此示例中，你在[编译配置](# Compiling the configuration)时将节点名称作为 $ComputerName 参数进行传递，从而指定节点名称。 该名称默认为“localhost”。

## 正在编译配置
必须将其编译为 MOF 文档才能执行配置。 你可通过调用配置（像调用 PowerShell 函数一样）以执行此操作。
>__注意：__若要调用配置，该函数必须在全局范围内（与任何其他 PowerShell 函数一样）。 可通过以下方式来实现此操作：对脚本执行“dot-source”操作，或者使用 F5 或单击 ISE 中的“运行脚本”按钮以运行配置脚本。 若要对脚本执行“dot-source”操作，请运行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含配置的脚本文件的名称。

调用配置时，将创建：

- 与配置名称相同的位于当前目录的文件夹。
- 新目录中名为 _NodeName_.mof 的文件，其中 _NodeName_ 为配置的目标节点名称。 如果有多个节点，则将为每个节点创建 MOF 文件。

>__请注意__：此 MOF 文件包含目标节点的所有配置信息。 因此，务必确保其安全性。 有关详细信息，请参阅[保护 MOF 文件](secureMOF.md)。

编译上述第一个配置会形成以下文件夹结构：

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

如果配置采用了参数（如示例 2 所述），则需在编译时提供该参数。 其形式如下：

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -ComputerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## 使用 DependsOn
有效的 DSC 关键字为 __DependsOn__。 通常（但不一定总是），DSC 将按资源在配置中显示的顺序来应用这些资源。 但是，由 __DependsOn__ 指定哪些资源依赖于其他资源，而 LCM 则确保这些资源的应用顺序正确（无论资源实例是以何种顺序定义的）。 例如，配置可能会指定__用户__资源实例依赖于__组__实例的存在：

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}
```

## 在配置中使用新的资源
如果运行了前面的示例，你可能注意到你已收到警告信息，提示你正在使用未显式导入的资源。
现在，DSC 附带 12 种资源作为 PSDesiredStateConfiguration 模块的一部分。 外部模块中的其他资源须置于 `$env:PSModulePath` 中以便 LCM 能够识别。 新的 cmdlet - [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)，可用来确定哪些资源已安装在系统上并且可供 LCM 使用。 
一旦这些模块已置于 `$env:PSModulePath` 中并由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 正确识别，你仍需在配置中加载它们。 __Import-DscResource__ 是仅可在__配置__块中识别的动态关键字（即它不是 cmdlet）。 __Import-DscResource__ 支持两种参数：
* __ModuleName__ 是使用 __Import-DscResource__ 的推荐方法。 它接受包含要导入资源的模块名称以及模块名称的字符串数组。 
* __Name__ 是要导入资源的名称。 这不是由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 返回为“Name”的友好名称，而是定义资源架构时使用的类名（由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 返回为 __ResourceType__）。 

## 另请参阅
* [Windows PowerShell Desired State Configuration 概述](overview.md)
* [DSC 资源](resources.md)
* [配置本地配置管理器](metaConfig.md)



<!--HONumber=May16_HO3-->


