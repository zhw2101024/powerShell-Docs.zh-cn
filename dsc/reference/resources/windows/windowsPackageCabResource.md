---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsPackageCab 资源
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076933"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab 资源

> 适用于：Windows PowerShell 5.1 及更高版本

Windows PowerShell Desired State Configuration (DSC) 中的 WindowsPackageCab 资源提供了一种机制，用于在目标节点上安装或卸载 Windows Cabinet (.cab) 程序包。

目标节点必须已安装 DISM PowerShell 模块。 有关信息，请参阅[在 Windows PowerShell 中使用 DISM](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)。


## <a name="syntax"></a>语法

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   |
|---|---|
| 名称| 指明要确保其处于特定状态的程序包的名称。|
| Ensure| 指示程序包是否已安装。 将此属性设置为“Absent”以确保未安装程序包（如果已安装则卸载程序包）。 将其设置为“Present”（默认值）以确保已安装程序包。|
| 路径| 指示程序包所在的路径。|
| LogPath| 指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。|
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。|

## <a name="example"></a>示例

下面的示例配置需要使用输入参数，并确保安装了 `$Name` 参数指定的.cab 文件。

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```