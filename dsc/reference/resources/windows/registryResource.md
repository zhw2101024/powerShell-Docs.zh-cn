---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Registry 资源
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076950"
---
# <a name="dsc-registry-resource"></a>DSC Registry 资源

适用于：_Windows PowerShell 4.0 和 Windows PowerShell 5.0_

Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。

## <a name="syntax"></a>语法

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>“属性”

| 属性 | 说明 |
| --- | --- |
| 键| 指示要确保其特定状态的注册表项的路径。 路径必须包含配置单元。|
| ValueName| 指示注册表值的名称。 若要添加或删除注册表项，请将此属性指定为空字符串，无需指定 ValueType 或 ValueData。 若要修改或删除注册表项的默认值，请将此属性指定为空字符串，同时指定 ValueType 或 ValueData。|
| Ensure| 指示项和值是否存在。 将此属性设置为“Present”以确保其存在。 将此属性设置为“Absent”以确保其不存在。 默认值为“Present”。|
| Force| 如果指定的注册表项存在，**Force** 将用新值覆盖它。 如果删除包含子项的注册表项，这必须是 $true |
| Hex| 指示是否以十六进制格式表示数据。 如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。 对其他类型无效。 默认值为 **$false**。|
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。|
| ValueData| 注册表值的数据。|
| ValueType| 指示值的类型。 支持的类型有：字符串 (REG_SZ)、二进制 (REG-BINARY)、Dword 32 位 (REG_DWORD)、Qword 64 位 (REG_QWORD)、多字符串 (REG_MULTI_SZ)、可扩充字符串 (REG_EXPAND_SZ) |

## <a name="example"></a>示例

此示例确保名为“ExampleKey”的键存在于 **HKEY\_LOCAL\_MACHINE** 配置单元中。

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> 必须使用用户凭据运行配置，而不是以系统身份运行，才能在 `HKEY\CURRENT\USER` 配置单元中更改注册表设置。 可以使用 **PsDscRunAsCredential** 属性来指定配置的用户凭据。 有关示例，请参阅[使用用户凭据运行 DSC](../../../configurations/runAsUser.md)。
