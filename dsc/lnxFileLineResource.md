---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "适用于 Linux nxFileLine 资源的 DSC"
ms.openlocfilehash: 281f08c1dbf42372762a2b1b9838427b910ea791
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a>适用于 Linux nxFileLine 资源的 DSC

PowerShell Desired State Configuration (DSC) 中的 **nxFileLine** 资源提供了管理 Linux 节点上配置文件中的行的机制。

## <a name="syntax"></a>语法

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>“属性”

|  属性 |  说明 | 
|---|---|
| 文件路径| 要管理其在目标节点上的行的文件的完整路径。| 
| ContainsLine| 要确保存在于文件中的行。 如果此行不存在于文件中，则将其追加到该文件中。 **ContainsLine** 为必填项，但是如不需要，则可将设置为空字符串 (ContainsLine = ' ')。| 
| DoesNotContainPattern| 不应存在于此文件中的行的正则表达式模式。 将从文件中删除任何存在于此文件中并与正则表达式相匹配的行。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 

## <a name="example"></a>示例

此示例演示如何使用 **nxFileLine** 资源来配置 `/etc/sudoers` 文件，从而确保将用户 monuser 配置为“not requiretty”。

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

