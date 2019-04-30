---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 从正在运行的进程解码 PowerShell 命令
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086232"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>从正在运行的进程解码 PowerShell 命令

有时，你可能有一个正在运行的 PowerShell 进程占用了大量资源。
此进程可以在[任务计划程序][]作业或 [SQL Server 代理][]作业的上下文中运行。 在运行多个 PowerShell 进程的位置，很难知道哪个进程表示问题。 本文演示了如何解码 PowerShell 进程当前运行的脚本块。

## <a name="create-a-long-running-process"></a>创建一个长时间运行的进程

要演示此场景，请打开一个新的 PowerShell 窗口并运行以下代码。 它执行一个 PowerShell 命令，每分钟输出一个数字，持续 10 分钟。

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

PowerShell 正在执行的命令正文存储在 [Win32_Process][] 类的 CommandLine 属性中。 如果命令是[编码命令][]，则 CommandLine 属性包含字符串“EncodedCommand”。 使用此信息，可以通过以下进程取消对编码命令的模糊处理。

以管理员身份启动 PowerShell。 以管理员身份运行 PowerShell 至关重要，否则在查询正在运行的进程时不会返回任何结果。

执行以下命令以获取所有具有编码命令的 PowerShell 进程：

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

下面的命令创建一个自定义 PowerShell 对象，其中包含进程 ID 和编码命令。

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

现在可以解码编码命令。 下面的代码片段循环访问命令详细信息对象、解码编码命令，并将解码后的命令添加回该对象，以便进一步研究。

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

现在可以通过选择解码后的命令属性来查看已解码的命令。

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
