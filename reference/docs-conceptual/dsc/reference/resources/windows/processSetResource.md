---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC ProcessSet 资源
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953124"
---
# <a name="dsc-processset-resource"></a>DSC ProcessSet 资源

> 适用于：Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **ProcessSet** 资源提供了用于在目标节点上配置进程的机制。

## <a name="syntax"></a>语法

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|路径 |进程可执行文件的路径。 如果这些是可执行文件的名称（不是完全限定的路径），则 DSC 资源会搜索环境 `$env:Path` 变量以查找文件。 如果此属性的值是完全限定的路径，则 DSC 不使用 `$env:Path` 环境变量查找文件，并且会在不存在任何路径时引发错误。 不允许使用相对路径。 |
|凭据 |指示启动进程的凭据。 |
|StandardErrorPath |进程写入标准错误的路径。 将覆盖任何现有文件。 |
|StandardInputPath |进程从中接收标准输入的流。 |
|StandardOutputPath |进程写入标准输出的文件的路径。 将覆盖任何现有文件。 |
|WorkingDirectory |用作进程当前工作目录的位置。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定进程是否存在。 将此属性设置为 **Present** 可确保进程存在。 否则，将其设置为 **Absent**。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。