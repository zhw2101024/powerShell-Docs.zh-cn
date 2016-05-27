---
title:  使用 Out Cmdlet 重定向数据
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  2a4acd33-041d-43a5-a3e9-9608a4c52b0c
---

# 使用 Out-* Cmdlet 重定向数据
Windows PowerShell 提供多个 cmdlet，可让你直接控制数据输出。 这些 cmdlet 具有两个重要的共同特征。

第一，它们通常将数据转换为某种形式的文本。 这样做的原因是它们将数据输出到需要文本输入的系统组件。 这意味着它们需要将对象表示为文本。 因此，文本的格式设置为你在 Windows PowerShell 控制台窗口中看到的形式。

第二，这些 cmdlet 使用 Windows PowerShell 谓词 **Out**，因为它们会将信息从 Windows PowerShell 发送到别处。 **Out-Host** cmdlet 也不例外：主机窗口显示在 Windows PowerShell 之外。 这一点尤为重要，原因是将数据发送出 Windows PowerShell 时，实际上已删除该数据。 在你尝试创建用于将数据分页到主机窗口的管道，然后尝试将其格式化为列表时，可以看到此内容，如下所示：

```
PS> Get-Process | Out-Host -Paging | Format-List
```

你可能希望命令显示列表格式的进程信息页。 但是，它将显示默认表格式列表：

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

**Out-Host** cmdlet 直接将数据发送到控制台，因此 **Format-List** 命令绝不会收到任何要进行格式化的内容。

构建此命令的正确方法是将 **Out-Host** cmdlet 置于管道末尾，如下所示。 这将导致进程数据先在列表中格式化，然后再分页和显示。

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

这适用于所有 **Out** cmdlet。 **Out** cmdlet 应始终出现在管道末尾。

> [!NOTE] 所有 **Out** cmdlet 都使用对控制台窗口有效的格式（包括行长度限制）将输出呈现为文本。

#### 分页控制台输出 (Out-Host)
默认情况下，Windows PowerShell 将数据发送到主机窗口，这正是 Out-Host cmdlet 的用途。 Out-Host cmdlet 的主要用途是对数据进行分页，如前面所述。 例如，下面的命令使用 Out-Host 对 Get-Command cmdlet 的输出进行分页：

```
PS> Get-Command | Out-Host -Paging
```

你还可以使用 **more** 函数对数据进行分页。 在 Windows PowerShell 中，**more** 是调用 **Out-Host -Paging** 的函数。 下面的命令演示了如何使用 **more** 函数对 Get-Command 的输出进行分页：

```
PS> Get-Command | more
```

如果将一个或多个文件名作为参数包括到 more 函数中，则该函数将读取指定文件并将其内容分页到主机中：

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### 放弃输出 (Out-Null)
**Out-Null** cmdlet 旨在用于立即放弃接收的任何输入。 这对放弃收到的不利于运行命令的不必要数据很有用。 键入下面的命令时，该命令不会返回任何内容：

```
PS> Get-Command | Out-Null
```

**Out-Null** cmdlet 不会放弃错误输出。 例如，如果输入下面的命令，则将显示一条消息，通知你 Windows PowerShell 无法识别“Is-NotACommand”：

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### 打印数据 (Out-Printer)
可以通过使用 **Out-Printer** cmdlet 打印数据。 如果未提供打印机名称，则 **Out-Printer** cmdlet 将使用默认打印机。 可以通过指定其显示名称使用任何基于 Windows 的打印机。 无需使用任何类型的打印机端口映射，甚至无需使用真正的物理打印机。 例如，如果安装了 Microsoft Office 文档映像工具，则可通过键入以下内容将数据发送到映像文件：

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### 保存数据 (Out-File)
可以使用 **Out-File** cmdlet 将输出发送到文件而不是控制台窗口。 下面的命令行将进程列表发送到文件 **C:\temp\processlist.txt**：

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

如果你习惯使用传统的输出重定向，则使用 **Out-File** cmdlet 可能与你的预期结果有所不同。 若要了解其行为，必须知道运行 **Out-File** cmdlet 的上下文。

默认情况下，**Out-File** cmdlet 创建 Unicode 文件。 从长远来看，这是最佳默认操作，但是它意味着应创建 ASCII 文件的工具将无法使用默认的输出格式正常运作。 可以使用 **Encoding** 参数将默认输出格式更改为 ASCII：

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** 将文件内容格式化为与控制台输出类似的形式。 这会导致输出被截断，大多数情况下正如它在控制台窗口中一样。 例如，如果运行下面的命令：

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

输出将如下所示：

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

若要使不会强制换行的输出与屏幕宽度匹配，可以使用 **Width** 参数来指定行宽。 因为 **Width** 是一个 32 位整数参数，因此其最大值可以是 2147483647。 键入以下内容以将行宽设置为此最大值：

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

想要保存原本显示在控制台中的输出时，使用 **Out-File** cmdlet 最有用。 若要更好地控制输出格式，需要更高级的工具。 我们将在下一章中查看这些内容以及有关对象操作的一些详细信息。



<!--HONumber=May16_HO2-->


