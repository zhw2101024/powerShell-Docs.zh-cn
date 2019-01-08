---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 从正在运行的进程解码 PowerShell 命令
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400394"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>从正在运行的进程解码 PowerShell 命令

有时，您可能必须运行的进程什么占用了大量的资源的 PowerShell。
可能的上下文中运行此过程[任务计划程序][]作业或[SQL Server 代理][]作业。 其中有多个运行的 PowerShell 进程，它可能很难知道哪个进程表示问题。 本文介绍如何对 PowerShell 进程当前正在运行的脚本块。

## <a name="create-a-long-running-process"></a>创建长时间运行进程

为了演示此方案中，打开新的 PowerShell 窗口并运行下面的代码。 它将执行的 PowerShell 命令的输出 10 分钟内每隔一分钟的数字。

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a>查看进程

执行的 PowerShell 命令的正文存储在**CommandLine**的属性[Win32_Process][]类。 如果该命令是[编码命令][]，则**CommandLine**属性包含字符串"EncodedCommand"。 使用此信息，该编码的命令可以是通过以下过程取消模糊处理。

以管理员身份启动 PowerShell。 非常重要，以管理员身份运行 PowerShell，否则不返回任何结果查询正在运行的进程时。

执行以下命令获取所有已编码的命令的 PowerShell 进程：

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

以下命令创建包含进程 ID 和编码命令的自定义 PowerShell 对象。

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

现在可以解码已编码的命令。 以下代码片段循环访问命令的详细信息对象、 解码已编码的命令，并将解码后的命令添加回以便进一步进行调查的对象。

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

现在可以选择已解码的 command 属性来查看已解码的命令。

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[任务计划程序]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server 代理]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[编码命令]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
