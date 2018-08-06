---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Log 资源
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268426"
---
# <a name="dsc-log-resource"></a>DSC Log 资源

适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 内的 __Log__ 资源提供了将消息写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的机制。

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> 默认情况下，仅启用 DSC 的运行日志。 必须先启用“分析”日志才能看到或使用它。 有关详细信息，请参阅 [DSC 事件日志在哪里？](troubleshooting.md#where-are-dsc-event-logs)。

## <a name="properties"></a>“属性”

| 属性 | 说明 |
| --- | --- |
| 消息| 指示要写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的消息。|
| DependsOn | 指示必须先运行其他资源的配置，再写入此日志消息。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = '[ResourceType]ResourceName'`。|

## <a name="example"></a>示例

下面的示例演示如何在 Microsoft-Windows-Desired State Configuration/Analytic 事件日志中纳入消息。

> [!NOTE]
> 如果在配置此资源后运行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它始终会返回 $false。

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```