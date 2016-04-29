---
title: 使用 Process Cmdlet 管理进程
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
---
# 使用 Process Cmdlet 管理进程
可以在 Windows PowerShell 中使用 Process cmdlet 来管理 Windows PowerShell 中的本地和远程进程。

## 获取进程 (Get-Process)
若要获取在本地计算机上运行的进程，请运行不具有参数的 **Get-Process**。

你可以通过指定其进程名称或进程 ID 来获取特定进程。 以下命令将获取空闲进程：

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

尽管某些情况下 cmdlet 不会返回任何数据很正常，但当你按其 ProcessId 指定一个进程时，如果未找到任何匹配项，**Get-Process** 将生成一个错误，因为通常的目的是检索一个已知的正在运行的进程。 如果按该 ID 找不到进程，则很可能该 ID 不正确或相关进程已退出：

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

你可以使用 Get-Process cmdlet 的 Name 参数来基于进程名称指定进程的子集。 Name 参数可以采用多个名称（在列表中以逗号分隔），并且支持使用通配符，因此，你可以键入名称模式。

例如，以下命令将获取名称以“ex”开头的进程。

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

由于 .NET System.Diagnostics.Process 类是 Windows PowerShell 进程的基础，因此它遵循 System.Diagnostics.Process 使用的某些约定。 其中一个约定是可执行文件的进程名从不在可执行文件名的末尾包含“.exe”。

**Get-Process** 还接受 Name 参数的多个值。

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

可以使用 Get-Process 的 ComputerName 参数获取远程计算机上的进程。 例如，以下命令将获取本地计算机（表示为“localhost”）和两台远程计算机上的 PowerShell 进程。

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

计算机名在此显示中不可见，但是它们存储在 Get-Process 返回的进程对象的 MachineName 属性中。 下面的命令使用 Format-Table cmdlet 显示进程对象的进程 ID、ProcessName 和 MachineName (ComputerName) 属性。

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

这一更为复杂的命令将 MachineName 属性添加到标准 Get-Process 显示中。 反撇号 (`)(ASCII 96) 是 Windows PowerShell 的继续符。

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## 停止进程 (Stop-Process)
Windows PowerShell 可以灵活地列出进程，但停止进程呢？

**Stop-Process** cmdlet 将采用 Name 或 ID 来指定想要停止的进程。 能否停止进程取决于你的权限。 某些进程无法停止。 例如，如果你尝试停止空闲进程，则会出现错误：

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

你也可以通过使用 **Confirm** 参数进行强制提示。 如果你在指定进程名称时使用通配符，此参数会特别有用，因为可能会意外地匹配到你不想要停止的一些进程：

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

可以通过使用某些对象筛选 cmdlet 来实现复杂的过程操作。 因为 Process 对象具有 Responding 属性，当程序不再响应时该属性为 true，你可以使用以下命令停止所有无响应的应用程序：

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

在其他情况下，可以使用相同的方法。 例如，假设用户启动另一个应用程序时，辅助通知区域的应用程序将自动运行。 你可能会发现在“终端服务”会话中它无法正常工作，但你仍想要将其保留在物理计算机控制台上运行的会话中。 连接到物理计算机桌面的会话始终具有一个为 0 的会话 ID，这样你可以通过使用 **Where-Object** 和进程 **SessionId** 停止在其他会话中的所有进程的实例：

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process cmdlet 不具有 ComputerName 参数。 因此，若要在远程计算机上运行停止进程，需要使用 Invoke-Command cmdlet。 例如，若要停止 Server01 远程计算器上的 PowerShell 进程，请键入：

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## 停止所有其他 Windows PowerShell 会话
这可能对停止当前会话之外的所有正在运行的 Windows PowerShell 会话偶尔有用。 如果会话正在使用过多资源或无法访问（它可能正在远程运行或在另一个桌面会话中运行），可能不能直接将其停止。 如果你尝试停止所有正在运行的会话，但是，这可能会终止当前会话。

每个 Windows PowerShell 会话都具有一个包含 Windows PowerShell 进程的 ID 的环境变量 PID。 你可以对比每个会话的 ID 检查 $PID，并仅终止具有不同 ID 的 Windows PowerShell 会话。 下面的管道命令执行此操作并返回终止的会话的列表（因为使用了 **PassThru** 参数）：

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## 启动、调试和等待进程
Windows PowerShell 还附带 cmdlet，以启动（或重启）、调试进程，并在运行命令之前等待进程完成。 有关这些 cmdlet 的信息，请参阅有关每个 cmdlet 的 cmdlet 帮助主题。

## 另请参阅
[Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)
[Stop-Process [m2]](assetId:///12454238-9881-457a-bde4-fb6cd124deec)
[Start-Process](assetId:///41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
[Wait-Process](assetId:///9222af7a-789d-4a09-aa90-09d7c256c799)
[Debug-Process](assetId:///eea1dace-3913-4dbd-b659-5a94a610eee1)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)



<!--HONumber=Apr16_HO1-->


