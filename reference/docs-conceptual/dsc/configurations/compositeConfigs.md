---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 嵌套配置
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417869"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="537b1-103">嵌套 DSC 配置</span><span class="sxs-lookup"><span data-stu-id="537b1-103">Nesting DSC configurations</span></span>

<span data-ttu-id="537b1-104">嵌套配置（也称为复合配置）是在其他配置中进行调用的配置，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="537b1-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="537b1-105">两个配置必须在同一文件中定义。</span><span class="sxs-lookup"><span data-stu-id="537b1-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="537b1-106">让我们看一个简单的示例：</span><span class="sxs-lookup"><span data-stu-id="537b1-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="537b1-107">在这个示例中，`FileConfig` 采用两个强制参数 CopyFrom  和 CopyTo  ，它们在 `File` 资源块中用作 SourcePath  和 DestinationPath  属性的值。</span><span class="sxs-lookup"><span data-stu-id="537b1-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="537b1-108">`NestedConfig` 配置调用 `FileConfig`，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="537b1-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="537b1-109">`NestedConfig` 资源块中的属性（**CopyFrom** 和 **CopyTo**）是 `FileConfig` 配置的参数。</span><span class="sxs-lookup"><span data-stu-id="537b1-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="537b1-110">DSC 当前不支持嵌套配置中的嵌套配置。</span><span class="sxs-lookup"><span data-stu-id="537b1-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="537b1-111">只能将配置嵌套一层。</span><span class="sxs-lookup"><span data-stu-id="537b1-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="537b1-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="537b1-112">See Also</span></span>

- [<span data-ttu-id="537b1-113">复合资源：将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="537b1-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)