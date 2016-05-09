---
title: 使用格式命令更改输出视图
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
---
# 使用格式命令更改输出视图
Windows PowerShell 具有一组 cmdlet，可让你控制要显示的特定对象的属性。 所有 cmdlet 的名称都以谓词 **Format** 开头。 它们使你可以选择要显示的一个或多个属性。

**Format** cmdlet 包括 **Format-Wide**、**Format-List**、**Format-Table** 和 **Format-Custom**。 在本用户指南中，我们将只介绍 **Format-Wide**、**Format-List** 和 **Format-Table** cmdlet。

如果不指定要显示的特定属性，则每个 format cmdlet 都具有要使用的默认属性。 各 cmdlet 也使用相同的参数名称，**Property**，来指定要显示的属性。 因为 **Format-Wide** 只显示单个属性，其 **Property** 参数仅采用单个值，但 **Format-List** 和 **Format-Table** 的属性参数接受一系列属性名称。

如果你将命令 **Get-Process-Name powershell** 与 Windows PowerShell 运行的两个实例搭配使用，你将得到如下所示的输出：

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

在本部分接下来的内容中，我们将探究如何使用 **Format** cmdlet 更改此命令的输出的显示方式。

### 将 Format-Wide 用于 Single-Item 输出
默认情况下，**Format-Wide** 只显示对象的默认属性。 与每个对象关联的信息将显示在单个列中：

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

你还可以指定非默认属性：

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### 使用列控制 Format-Wide 显示
使用 **Format-Wide** cmdlet，每次只能显示一个属性。 这对于显示每行只显示一个元素的简单列表很有用。 若要获取简单列表，通过键入以下内容将 **Column** 参数的值设为 1：

```
Get-Command Format-Wide -Property Name -Column 1
```

### 将 Format-List 用于列表视图。
**Format-List** cmdlet 以列表的形式显示对象，同时标记每个属性并在单独的行上显示：

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

你可以指定所需数目的属性：

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### 通过将 Format-List 与通配符搭配使用获取详细信息
**Format-List** cmdlet 使你可以将通配符用作其 **Property** 参数的值。 这样便可以显示详细信息。 通常情况下，对象包含的信息比你需要的多，这就是默认情况下 Windows PowerShell 不显示所有属性值的原因。 若要显示对象的全部属性，则使用 **Format-List-Property \&#42;** 命令。 下面的命令针对单个进程生成超过 60 行的输出：

```
Get-Process -Name powershell | Format-List -Property *
```

虽然 **Format-List** 命令对显示详细信息很有用，但如果你想要包括多个项目的输出的概述，更常用的是一个更简单的表格视图。

### 将 Format-Table 用于表格输出
如果你在没有指定属性名称的情况下使用 **Format-Table** cmdlet 来格式化 **Get-Process** 命令的输出，你所得到的输出会和未执行任何格式设置时得到的完全一样。 原因是进程通常以表格格式显示，和大多数 Windows PowerShell 对象一样。

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### 改进 Format-Table 输出（自动调整大小）
尽管表格视图对显示大量可比较的信息很有用，但如果显示区域对于数据来说太窄，则可能导致数据难以理解。 例如，如果你尝试显示进程路径、ID、名称和公司，你获得的却是进程路径和公司列的截断了的输出：

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

当你运行 **Format-Table** 命令时，如果你指定 **AutoSize** 参数，Windows PowerShell 会根据你要显示的实际数据来计算列宽。 这使得**路径**列可读，但公司列将仍保持截断状态：

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** cmdlet 仍可能会截断数据，但仅会在屏幕的末尾处进行截断。 除最后一个显示的属性外，会让所有属性获得各自所需的大小，以使最长的数据元素得以正确显示。 如果你交换**属性**值列表中**路径**和**公司**的位置，你会发现公司名称是可见的，但路径则被截断：

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** 命令假定属性距离属性列表的开头越近，则该属性越重要。 因此，它会尝试完整显示离列表开头最近的那些属性。 如果 **Format-Table** 命令无法显示所有属性，它将从显示中删除某些列，并发出警告。 如果你使**名称**变成列表中的最后一个属性，便可以看到这一行为：

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

在上面的输出中，将截断 ID 列以使其适合列表，并叠加列标题。 自动调整列大小不会始终执行所需的操作。

#### 让列中的 Format-Table 输出自动换行 (Wrap)
你可以通过使用 **Wrap** 参数让较长的 **Format-Table** 数据在其显示列中自动换行。 仅使用 **Wrap** 参数不一定会实现所需的操作，因为如果你不同时指定 **AutoSize**，它会使用默认设置：

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

使用 **Wrap** 参数的一个优点是基本不会减慢进程速度。 如果你对大型目录系统执行递归文件列表，那么如果你使用 **AutoSize**，可能得耗用大量时间和内存，才能显示第一批输出项。

如果你并不关心系统负载，那么结合使用 **AutoSize** 和 **Wrap** 参数则会获得良好的效果。 会始终向初始列分配其所需的宽度以使其中的项显示在一行上，就和你指定 **AutoSize** 而不使用 **Wrap** 参数的效果一样。 唯一的不同是最后一列将自动换行（如有必要的话）：

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

如果你先指定最宽的列，则某些列可能无法显示，因此最安全的做法是先指定最小的数据元素。 在下面的示例中，我们首先指定特别宽的路径元素，甚至使用自动换行，但仍丢失了最后的**名称**列：

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### 组织选项卡输出 (-GroupBy)
用于表格输出控制的另一个有用参数是 **GroupBy**。 较长的列表可能尤其难以进行比较。 **GroupBy** 参数基于属性值对输出进行分组 例如，我们可以按公司对进程分组以便于检查，同时从属性列表中省略公司的值：

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```



<!--HONumber=Apr16_HO1-->


