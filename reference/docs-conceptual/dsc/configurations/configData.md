---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用配置数据
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954184"
---
# <a name="using-configuration-data-in-dsc"></a>使用 DSC 中的配置数据

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

通过使用内置 DSC **ConfigurationData** 参数，可以定义可在配置中使用的数据。
这样一来，便可创建可用于多个节点或不同环境的单个配置。
例如，如果要开发应用程序，可将一个配置同时用于开发和生产环境，并使用配置数据指定每个环境的数据。

本主题介绍了 ConfigurationData  哈希表的结构。
有关如何使用配置数据的示例，请参阅[分离配置和环境数据](separatingEnvData.md)。

## <a name="the-configurationdata-common-parameter"></a>ConfigurationData 常见参数

DSC 配置使用在编译配置时指定的常见参数 ConfigurationData  。
有关编译配置的信息，请参阅 [DSC 配置](configurations.md)。

ConfigurationData 参数是必须具有至少一个名为 AllNodes 的键的哈希表   。
它还可以额外包含一个或多个键。

> [!NOTE]
> 除了名为“AllNodes”的键之外，本主题中的示例还额外使用一个名为 `NonNodeData` 的键。不过，可以额外添加任意数量的键，并能根据需要随意命名这些键  。

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

若要将属性应用到所有节点，可创建 **NodeName** 为 `*` 的 **AllNodes** 数组的成员。
例如，若要让每个节点具有 `LogPath` 属性，可以执行如下操作：

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

可以将 ConfigurationData  定义为与配置同属一个脚本文件的变量（如上面的示例所示），也可以定义为单独的 `.psd1` 文件中的变量。
若要在 `.psd1` 文件中定义 ConfigurationData  ，请创建仅包含表示配置数据的哈希表的文件。

例如，可创建一个名为 `MyData.psd1` 的文件，此文件包含以下内容：

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>编译包含配置数据的配置

若要编译已为其定义配置数据的配置，请以 ConfigurationData  参数值的形式传递配置数据。

这将为 AllNodes  数组中的每一条目都创建一个 MOF 文件。
每个 MOF 文件都使用相应数组条目的 `NodeName` 属性进行命名。

例如，如果将配置数据定义为位于上面的 `MyData.psd1` 文件中，编译配置将创建 `VM-1.mof` 和 `VM-2.mof` 文件。

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>使用变量编译包含配置数据的配置

若要使用定义为与配置同属一个 `.ps1` 文件的变量的配置数据，请在编译配置时将变量名称作为 ConfigurationData  参数值进行传递：

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>使用数据文件编译包含配置数据的配置

若要使用 .psd1 文件中定义的配置数据，可在编译配置时，将该文件的路径和名称作为 **ConfigurationData** 参数的值传递：

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>在配置中使用 ConfigurationData 变量

DSC 提供以下几种可在配置脚本中使用的特殊变量：

- **$AllNodes** 指 **ConfigurationData** 中定义的整个节点集合。 可使用 **.Where()** 和 **.ForEach()** 筛选 **AllNodes** 集合。
- **ConfigurationData** 指编译配置时，作为参数传递的整个哈希表。
-  MyTypeName 包含使用了变量的[配置](configurations.md)名称。 例如，在配置 `MyDscConfiguration` 中，`$MyTypeName` 的值将为 `MyDscConfiguration`。
- **Node** 指使用 **.Where()** 或 **.ForEach()** 筛选 **AllNodes** 集合后，该集合中的特定项。
  - 可阅读 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 了解有关这些方法的详细信息

## <a name="using-non-node-data"></a>使用非节点数据

如上面的示例所示，除了必需的 AllNodes  键之外，ConfigurationData  哈希表还可以额外包含一个或多个键。
本主题中的示例只额外使用了一个节点，并将它命名为“`NonNodeData`”。
不过，可以额外定义任意数量的键，并能根据需要随意命名这些键。

有关使用非节点数据的示例，请参阅[分离配置和环境数据](separatingEnvData.md)。

## <a name="see-also"></a>另请参阅

- [配置数据中的凭据选项](configDataCredentials.md)
- [DSC 配置](configurations.md)