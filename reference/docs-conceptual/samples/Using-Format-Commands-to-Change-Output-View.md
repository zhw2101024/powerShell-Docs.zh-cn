---
ms.date: 10/22/2019
keywords: powershell,cmdlet
title: 使用格式命令更改输出视图
ms.openlocfilehash: 9d9854362b5150a99bdd0c02518599840c1fd42d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444427"
---
# <a name="using-format-commands-to-change-output-view"></a>使用格式命令更改输出视图

PowerShell 具有一组 cmdlet，可让你控制特定对象的属性的显示方式。 所有 cmdlet 的名称都以谓词 `Format` 开头。 它们使你可以选择要显示的属性。

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

本文介绍 `Format-Wide`、`Format-List` 和 `Format-Table` cmdlet。

PowerShell 中的每个对象类型都具有未指定要显示的属性时使用的默认属性。 各 cmdlet 也使用相同的 Property 参数，来指定要显示的属性  。 因为 `Format-Wide` 只显示单个属性，其 Property 参数仅采用单个值，但 `Format-List` 和 `Format-Table` 的属性参数接受一系列属性名称  。

在此示例中，`Get-Process` cmdlet 的默认输出显示，我们有两个正在运行的 Internet Explorer 实例。

```powershell
Get-Process -Name iexplore
```

Process 对象的默认格式显示如下属性  ：

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>将 Format-Wide 用于 Single-Item 输出

默认情况下，`Format-Wide` cmdlet 只显示对象的默认属性。 与每个对象关联的信息将显示在单个列中：

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

你还可以指定非默认属性：

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>使用列控制 Format-Wide 显示

使用 `Format-Wide` cmdlet 时，每次只能显示一个属性。 这可用于在多个列中显示大型列表。

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>将 Format-List 用于列表视图

`Format-List` cmdlet 以列表的形式显示对象，同时标记每个属性并在单独的行上显示：

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

你可以指定所需数目的属性：

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>通过将 Format-List 与通配符搭配使用获取详细信息

`Format-List` cmdlet 使你可以将通配符用作其 Property 参数的值  。 这样便可以显示详细信息。 通常情况下，对象包含的信息比你需要的多，这就是默认情况下 PowerShell 不显示所有属性值的原因。 若要显示对象的全部属性，则使用 **Format-List-Property \&#42;** 命令。 下面的命令针对单个进程生成超过 60 行的输出：

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

虽然 `Format-List` 命令对显示详细信息很有用，但如果你想要包括多个项目的输出的概述，更常用的是一个更简单的表格视图。

## <a name="using-format-table-for-tabular-output"></a>将 Format-Table 用于表格输出

如果你在没有指定属性名称的情况下使用 `Format-Table` cmdlet 来格式化 `Get-Process` 命令的输出，你所得到的输出会和未使用 `Format` cmdlet 执行任何格式设置时得到的完全一样。 默认情况下，PowerShell 以表格格式显示 Process 对象  。

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>改进 Format-Table 输出（自动调整大小）

尽管表格视图对显示大量信息很有用，但如果显示区域对于数据来说太窄，则可能导致数据难以理解。 在上面的示例中，输出被截断。 当你运行 `Format-Table` 命令时，如果你指定 AutoSize  参数，PowerShell 会根据显示的实际数据来计算列宽。 这使得列可读。

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

`Format-Table` cmdlet 仍可能会截断数据，但仅会在屏幕的末尾处进行截断。 除最后一个显示的属性外，会让所有属性获得各自所需的大小，以使最长的数据元素得以正确显示。

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

`Format-Table` 命令假设按重要性顺序列出属性。 因此，它会尝试完整显示离列表开头最近的那些属性。 如果 `Format-Table` 命令无法显示所有属性，则会从显示中删除某些列。 可以在 DependentServices 属性前一个示例中查看此行为  。

### <a name="wrapping-format-table-output-in-columns-wrap"></a>让列中的 Format-Table 输出自动换行 (Wrap)

可以通过使用 Wrap 参数让较长的 `Format-Table` 数据在其显示列中自动换行  。 使用 Wrap 参数可能不会实现所需的操作，因为如果你不同时指定 AutoSize，它会使用默认设置   ：

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

使用 Wrap 参数基本不会减慢进程速度  。 但是，使用 AutoSize 格式化大型目录结构的递归文件列表可能得耗用大量时间和内存，才能显示第一批输出项  。

如果你并不关心系统负载，那么结合使用 AutoSize 和 Wrap 参数则会获得良好的效果   。
初始列仍根据需要最大限度地使用宽度来在一行上显示项，但在必要时将最后一列换行。

> [!NOTE]
> 当你首先指定最宽的列时，可能不会显示某些列。 为了获得最佳结果，请先指定最小的数据元素。

在下面的示例中，我们首先指定最宽的属性。

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

即使进行了换行，也会省略最后 ID 列  ：

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>组织选项卡输出 (-GroupBy)

用于表格输出控制的另一个有用参数是 **GroupBy**。 较长的列表可能尤其难以进行比较。 **GroupBy** 参数基于属性值对输出进行分组 例如，我们可以按 StartType 对服务分组以便于检查，同时从属性列表中省略 StartType 值   ：

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
