---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "嵌套配置"
ms.openlocfilehash: 89badda86707a129909b1c3cc3f79afa0b5f5df6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-dsc-configurations"></a>嵌套 DSC 配置

嵌套配置（也称为复合配置）是在其他配置中进行调用的配置，就像它是资源一样。
两个配置必须在同一文件中定义。

让我们看一个简单的示例：

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

在这个示例中，`FileConfig` 采用两个强制参数 **CopyFrom** 和 **CopyTo**，它们在 `File` 资源块中用作 **SourcePath** 和 **DestinationPath** 属性的值。 `NestedConfig` 配置调用 `FileConfig`，就像它是资源一样。
`NestedConfig` 资源块中的属性（**CopyFrom** 和 **CopyTo**）是 `FileConfig` 配置的参数。

## <a name="see-also"></a>另请参阅

- [复合资源：将 DSC 配置用作资源](authoringResourceComposite.md)

