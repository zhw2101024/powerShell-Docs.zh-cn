---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 配置
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080163"
---
# <a name="dsc-configurations"></a>DSC 配置

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

DSC 配置是定义某一特殊类型函数的 PowerShell 脚本。
若要定义配置，你可使用 PowerShell 关键字 **Configuration**。

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

将脚本保存为 `.ps1` 文件。

## <a name="configuration-syntax"></a>配置语法

配置脚本由以下部分组成：

- **配置**块。 这是最外层的脚本块。 你可通过使用 **Configuration** 关键字并提供配置名进行定义。 在这种情况下，该配置名为“MyDscConfiguration”。
- 一个或多个**节点**块。 这些将定义正在配置的节点（计算机或 VM）。 在以上配置中，有一个以计算机为目标的名为“TEST-PC1”的**节点**块。 节点块可以接受多个计算机名称。
- 一个或多个资源块。 这是此配置为其正在配置的资源设置属性的位置。 在这种情况下，有两个资源块，每个资源块都调用“WindowsFeature”资源。

在**配置**块中，可执行在 PowerShell 函数中通常可执行的任何操作。 例如，在上一示例中，如果不想在配置中对目标计算机名进行硬编码，则可以为节点名添加参数：

在此示例中，指定节点名称，具体方法为在编译配置时以 ComputerName  参数的形式传递节点名称。 该名称默认为“localhost”。

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

 节点块还可以接受多个计算机名称。 在上述示例中，可以使用 `-ComputerName` 参数，也可以将以逗号分隔的计算机列表直接传递到节点  块。

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

将计算机列表从配置指定到节点  块时，需要使用数组表示法。

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>正在编译配置

必须将其编译为 MOF 文档才能执行配置。
可通过调用配置（像调用 PowerShell 函数一样）来执行此操作。
此示例的最后一行仅包含配置名称，用于调用配置。

> [!NOTE]
> 函数必须在全局范围内（与其他任何 PowerShell 函数一样），才能调用配置。
> 可通过以下方式来实现此操作：对脚本执行“dot-source”操作，或者使用 F5 或单击 ISE 中的“运行脚本”  按钮以运行配置脚本。
> 若要对脚本执行“dot-source”操作，请运行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含配置的脚本文件的名称。

调用配置时，它会：

- 解析所有变量
- 在当前目录中使用与配置相同的名称创建文件夹。
- 在新目录中创建名为 _NodeName_.mof 的文件，其中 _NodeName_ 为配置的目标节点名称。
  如果有多个节点，则将为每个节点创建一个 MOF 文件。

> [!NOTE]
> MOF 文件包含目标节点的所有配置信息。 因此，务必确保其安全性。
> 有关详细信息，请参阅[保护 MOF 文件](../pull-server/secureMOF.md)。

编译上述第一个配置会形成以下文件夹结构：

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

如果配置采用了参数（如示例 2 所述），则需在编译时提供该参数。 其形式如下：

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>在配置中使用新的资源

如果运行了前面的示例，你可能注意到你已收到警告信息，提示你正在使用未显式导入的资源。
现在，DSC 附带 12 种资源作为 PSDesiredStateConfiguration 模块的一部分。

cmdlet - [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)，可用来确定哪些资源已安装在系统上并且可供 LCM 使用。
一旦这些模块已置于 `$env:PSModulePath` 中并由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 正确识别，你仍需在配置中加载它们。

 Import-DscResource 是仅可在配置  块中识别的动态关键字，它不是 cmdlet。
**Import-DscResource** 支持两种参数：

- **ModuleName** 是使用 **Import-DscResource** 的推荐方法。 它接受包含要导入资源的模块名称以及模块名称的字符串数组。
- **Name** 是要导入资源的名称。 这不是由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 返回为“Name”的友好名称，而是定义资源架构时使用的类名（由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 返回为 **ResourceType**）。

有关使用 `Import-DSCResource` 的详细信息，请参阅[使用 Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 差异

DSC 资源需要在 PowerShell 4.0 中存储的位置存在差异。 有关详细信息，请参阅[资源位置](import-dscresource.md#resource-location)。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell Desired State Configuration 概述](../overview/overview.md)
- [DSC 资源](../resources/resources.md)
- [配置本地配置管理器](../managing-nodes/metaConfig.md)
