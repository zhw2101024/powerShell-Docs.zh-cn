---
ms.date: 3/18/2019
title: 使用 FilterHashtable 创建 Get-WinEvent 查询
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058791"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>使用 FilterHashtable 创建 Get-WinEvent 查询

请参阅[通过 PowerShell 使用 FilterHashTable 筛选事件日志](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)，以查看 2014 年 6 月 3 日的原创“脚本专家”博客文章。

本文摘录自此原创博客文章，并说明了如何使用 `Get-WinEvent` cmdlet 的 FilterHashtable 参数筛选事件日志。 PowerShell 的 `Get-WinEvent` cmdlet 是一种功能强大的方法，可用于筛选 Windows 事件和诊断日志。 `Get-WinEvent` 查询使用 FilterHashtable 参数时，性能将得到改进。

处理大型事件日志时，如果将对象沿管道下发到 `Where-Object` 命令，效率将较低。 在 PowerShell 6 之前，`Get-EventLog` cmdlet 曾是另一个用于获取日志数据的方法。 例如，使用下面的命令筛选 Microsoft-Windows-Defrag 日志时，效率较低：

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

下面的命令使用了可提升性能的哈希表：

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>关于枚举的博客文章

本文提供了如何在哈希表中使用枚举值的相关信息。 有关枚举的详细信息，请参阅“脚本专家”博客文章。 若要创建用于返回枚举值的函数，请参阅[枚举和值](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)。
有关详细信息，请参阅[关于枚举的“脚本专家”系列博客文章](https://devblogs.microsoft.com/scripting/?s=about+enumeration)。

## <a name="hash-table-keyvalue-pairs"></a>哈希表键值对

若要生成高效查询，请将 `Get-WinEvent` cmdlet 和 FilterHashtable 参数结合使用。
FilterHashtable 允许哈希表作为筛选器，以从 Windows 事件日志获取特定信息。 哈希表将使用键值对。 有关哈希表的详细信息，请参阅 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。

键值对均位于同一行时，必须使用分号将它们分隔开来。 每个键值对位于单独的行时，则无需使用分号。 例如，本文将键值对均放置在单独的行上，因此未使用分号。

本示例使用多个 FilterHashtable 参数的键值对。 完成的查询包括 LogName、ProviderName、Keywords、ID 和 Level。

下表显示了允许的键值对，关于 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
FilterHashtable 参数的文档也包含这些键值对。

下表显示了键名称、数据类型以及数据值是否接受通配符。

| 键名称     | 值数据类型    | 是否接受通配符？ |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | 是 |
| ProviderName | `<String[]>`       | 是 |
| 路径         | `<String[]>`       | 否  |
| Keywords     | `<Long[]>`         | 否  |
| ID           | `<Int32[]>`        | 否  |
| 层次        | `<Int32[]>`        | 否  |
| StartTime    | `<DateTime>`       | 否  |
| EndTime      | `<DateTime>`       | 否  |
| UserID       | `<SID>`            | 否  |
| 数据         | `<String[]>`       | 否  |
| *            | `<String[]>`       | 否  |

## <a name="building-a-query-with-a-hash-table"></a>使用哈希表生成查询

若要验证结果并解决问题，它帮助生成一次包含一个键值对的哈希表。 查询从“Application”日志获取数据。 哈希表等效于 `Get-WinEvent –LogName Application`。

首先创建 `Get-WinEvent` 查询。 使用 FilterHashtable 参数的键值对，其中键为“LogName”，值为“Application”。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

继续使用 ProviderName 键生成哈希表。 ProviderName 是在“Windows 事件查看器”的“源”字段中显示的名称。 例如，下面的屏幕截图中的“.NET 运行时”：

![“Windows 事件查看器”源的图片。](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

更新哈希表，并包含键为 **ProviderName 且值为 .NET 运行时的键值对。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

若查询需要从存档的事件日志获取数据，请使用 Path 键。 Path 值指定日志文件的完整路径。 有关详细信息，请参阅“脚本专家”博客文章[使用 PowerShell 分析保存的事件日志以查找错误](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)。

## <a name="using-enumerated-values-in-a-hash-table"></a>在哈希表中使用枚举值

Keywords 是哈希表中的下一个键。 Keywords 数据类型是一个包含大量数字的 `[long]` 值类型的数组。 使用下面的命令查找 `[long]` 的最大值：

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

对于 Keywords 键，PowerShell 使用数字，而不是字符串（如 Security）。 “Windows 事件查看器”将 Keywords 显示为字符串，但它们是枚举值。 在哈希表中使用包含字符串值的 Keywords 键时，将显示错误消息。

打开“Windows 事件查看器”，从“操作”窗格单击“筛选当前日志”。
“关键字”下拉菜单将显示可用的关键字，如下面的屏幕截图所示：

![“Windows 事件查看器”关键字的图片。](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

使用下面的命令显示 `StandardEventKeywords` 属性名称。

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

枚举值将记录在 .NET Framework 中。 有关详细信息，请参阅 [StandardEventKeywords 枚举](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)。

Keywords 名称和枚举值如下所示：

| 名称             |  值            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| 无             | 0                 |

更新哈希表，并包含键为 Keywords 且 EventLogClassic 枚举值为 36028797018963968 的键值对。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Keywords 静态属性值（可选）

枚举 Keywords 键，但可以在哈希表查询中使用静态属性名称。
必须使用 Value__ 属性将属性名称转换为值，而非使用返回值。

例如，下面的脚本就使用了 Value__ 属性。

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>按事件 ID 筛选

若要获取更多特定数据，请按事件 ID 筛选查询的结果。哈希表将“事件 ID”引用为键 ID，其值为特定的“事件 ID”。“Windows 事件查看器”将显示“事件 ID”。此示例使用“事件 ID 1023”。

更新哈希表，并包含键为 ID 且值为 1023 的键值对。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>按级别筛选

若要进一步优化结果并仅包含属于错误的事件，请使用 Level 键。
“Windows 事件查看器”将 Level 显示为字符串值，但它们是枚举值。 在哈希表中使用包含字符串值的 Level 键时，将显示错误消息。

Level 包含诸如“错误”、“警告”或“信息性”等值。 使用下面的命令显示 `StandardEventLevel` 属性名称。

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

枚举值将记录在 .NET Framework 中。 有关详细信息，请参阅 [StandardEventLevel 枚举](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)。

Level 键的名称和枚举值如下所示：

| 名称           | 值 |
| -------------- | ----- |
| Verbose        |   5   |
| 信息  |   4   |
| 警告        |   3   |
| 错误          |   2   |
| 严重       |   1   |
| LogAlways      |   0   |

完成的查询的哈希表包括 Level 键和值 2。

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>枚举中的 Level 静态属性（可选）

枚举 Level 键，但可以在哈希表查询中使用静态属性名称。
必须使用 Value__ 属性将属性名称转换为值，而非使用返回值。

例如，下面的脚本就使用了 Value__ 属性。

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```