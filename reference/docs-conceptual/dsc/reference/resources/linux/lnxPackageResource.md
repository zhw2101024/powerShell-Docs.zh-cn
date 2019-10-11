---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxPackage 资源
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954814"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>适用于 Linux 的 DSC nxPackage 资源

PowerShell Desired State Configuration (DSC) 中的 **nxPackage** 资源提供了在 Linux 节点上管理程序包的机制。

## <a name="syntax"></a>语法

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|名称 |要确保其特定状态的程序包的名称。 |
|PackageManager |支持的值包括 **yum**、**apt** 和 **zypper**。 指定安装程序包时要使用的程序包管理器。 如果指定了 **FilePath**，则将使用提供的路径安装程序包。 否则，将使用程序包管理器从预配置的存储库安装程序包。 如果既不提供 **PackageManager**，也不提供 **FilePath**，则将使用系统默认的程序包管理器。 |
|PackageGroup |如果为 `$true`，则 **Name** 应为用于 **PackageManager** 的包组的名称。 提供 **FilePath** 时，**PackageGroup** 无效。 |
|参数 |将完全按原样传输给程序包的参数字符串。 |
|ReturnCode |预期的返回代码。 如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。 |
|文件路径 |包所在的文件路径。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |确定是否检查程序包是否存在。 将此属性设置为 **Present** 可确保包存在。 将其设置为 **Absent** 可确保包不存在。 默认值为 **Present**。 |

## <a name="example"></a>示例

以下示例确保使用“Yum”包管理器在 Linux 计算机上安装了名为“httpd”的包。

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```