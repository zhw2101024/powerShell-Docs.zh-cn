---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsFeatureSet 资源
ms.openlocfilehash: 8a64168d9ad0d6a6c40eb0398cc734fa93a247dc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726793"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet 资源

> 适用于：Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeatureSet** 资源提供了确保在目标节点上添加或删除角色和功能的机制。
此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 `Name` 属性中指定的每个功能调用 [WindowsFeature 资源](windowsfeatureResource.md)。

要将一些 Windows 功能配置为相同状态时，请使用此资源。

## <a name="syntax"></a>语法

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   |
|---|---|
| 名称| 要确保添加或删除的角色或功能的名称。 这与 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet 的 **Name** 属性相同，并非角色或功能的显示名称。|
| 凭据| 要用于添加或删除角色或功能的凭据。|
| Ensure| 指示是否添加角色或功能。 若要确保添加角色或功能，请将此属性设置为“Present”。若要确保删除角色或功能，请将此属性设为“Absent”。|
| IncludeAllSubFeature| 将此属性设置为 **$true** 可包括通过 **Name** 属性指定的功能的所有所需子功能。|
| LogPath| 希望资源提供程序在其中记录操作的日志文件的路径。|
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|
| 源| 指示要用于安装的源文件的位置（如有必要）。|

## <a name="example"></a>示例

以下配置可确保安装 **Web 服务器** (IIS) 和 **SMTP 服务器**功能，以及各自的所有子功能。

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
