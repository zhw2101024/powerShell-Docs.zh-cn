---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "嵌套配置"
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="1962d-103">嵌套 DSC 配置</span><span class="sxs-lookup"><span data-stu-id="1962d-103">Nesting DSC configurations</span></span>

<span data-ttu-id="1962d-104">嵌套配置（也称为复合配置）是在其他配置中进行调用的配置，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="1962d-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="1962d-105">两个配置必须在同一文件中定义。</span><span class="sxs-lookup"><span data-stu-id="1962d-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="1962d-106">让我们看一个简单的示例：</span><span class="sxs-lookup"><span data-stu-id="1962d-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="1962d-107">在这个示例中，`FileConfig` 采用两个强制参数 **CopyFrom** 和 **CopyTo**，它们在 `File` 资源块中用作 **SourcePath** 和 **DestinationPath** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1962d-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="1962d-108">`NestedConfig` 配置调用 `FileConfig`，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="1962d-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="1962d-109">`NestedConfig` 资源块中的属性（**CopyFrom** 和 **CopyTo**）是 `FileConfig` 配置的参数。</span><span class="sxs-lookup"><span data-stu-id="1962d-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="1962d-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1962d-110">See Also</span></span>

- [<span data-ttu-id="1962d-111">复合资源：将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="1962d-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

