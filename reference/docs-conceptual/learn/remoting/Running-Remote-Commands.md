---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: 运行远程命令
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058907"
---
# <a name="running-remote-commands"></a>运行远程命令

可以使用单个 PowerShell 命令在一台或数百台计算机上运行命令。 Windows PowerShell 通过使用各种技术（包括 WMI、RPC 和 WS-Management）支持远程计算。

PowerShell Core 支持 WMI、WS-Management 和 SSH 远程处理。 不再支持 RPC。

有关在 PowerShell Core 中进行远程处理的详细信息，请参阅以下文章：

- [在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]
- [在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>无需配置即可进行 Windows PowerShell 远程处理

许多 Windows PowerShell cmdlet 都具有 ComputerName 参数，此参数可使你在一台或多台远程计算机上收集数据和更改设置。 这些 cmdlet 使用不同的通信协议，无需进行任何特殊配置即可在所有 Windows 操作系统上工作。

这些 cmdlet 包括：

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

通常情况下，支持无需特殊配置即可进行远程处理的 cmdlet 具有 ComputerName 参数，但不具有 Session 参数。 若要在会话中查找这些 cmdlet，请键入：

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell 远程处理

使用 WS-Management 协议，Windows PowerShell 远程处理使你可以在一台或多台远程计算机上运行任何 Windows PowerShell 命令。 你可以建立持久连接、启动交互会话并在远程计算机上运行脚本。

若要使用 Windows PowerShell 远程处理，必须配置远程计算机以进行远程管理。
有关详细信息（包括说明），请参阅[关于远程要求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。

一旦配置了 Windows PowerShell 远程处理，就会有许多远程处理策略可供你使用。
本文只列出了其中的几个策略。 有关详细信息，请参阅[关于远程](/powershell/module/microsoft.powershell.core/about/about_remote)。

### <a name="start-an-interactive-session"></a>启动交互会话

若要使用单台远程计算机启动交互会话，请使用 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet。
例如，若要使用 Server01 远程计算器启动交互会话，请键入：

```powershell
Enter-PSSession Server01
```

命令提示符更改为显示远程计算机的名称。 你在提示符中键入的任何命令都将在远程计算机上运行，并且结果将显示在本地计算机上。

若要结束交互会话，请键入：

```powershell
Exit-PSSession
```

有关 Enter-PSSession 和 Exit-PSSession cmdlet 的详细信息，请参阅：

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>运行远程命令

若要在一台或多台计算机上运行一个命令，请使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet。 例如，若要在 Server01 和 Server02 远程计算机上运行 [Get-UICulture ](/powershell/module/microsoft.powershell.utility/get-uiculture) 命令，请键入：

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

输出将返回到你的计算机。

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>运行脚本

若要在一台或多台远程计算机上运行脚本，请使用 `Invoke-Command` cmdlet 的 FilePath 参数。 该脚本必须在你的本地计算机上或可由其访问。 结果将返回到你的本地计算机。

例如，以下命令在远程计算机 Server01 和 Server02 上运行 DiskCollect.ps1 脚本。

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>建立持久连接

使用 `New-PSSession` cmdlet 在远程计算机上创建一个持久会话。 以下示例在 Server01 和 Server02 上创建远程会话。 会话对象存储在 `$s` 变量中。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

建立会话后，你可以在这些会话中运行任何命令。 此外，由于会话是持久的，因此你可以从一个命令收集数据，并在另一个命令中使用它。

例如，下面的命令在 $s 变量中的会话中运行 Get-Hotfix 命令，并且它将结果保存在 $h 变量中。 将在 $s 中的每个会话中创建 $h 变量，但它不会存在于本地会话中。

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

现在，可以将 `$h` 变量中的数据与同一会话中的其他命令一起使用。 结果将显示在本地计算机上。 例如：

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>高级远程处理

Windows PowerShell 远程管理就在此处开始。 通过使用随 Windows PowerShell 一起安装的 cmdlet，你可以从本地和远程端点建立和配置远程会话、创建自定义和受限制的会话、允许用户从实际在远程会话上隐式运行的远程会话中导入命令、配置远程会话的安全性等。

Windows PowerShell 包含一个 WSMan 提供程序。 提供程序创建 `WSMAN:` 驱动器，允许你在本地计算机和远程计算机上的配置设置层次结构之间导航。

有关 WSMan 提供程序的详细信息，请参阅 [WSMan 提供程序](https://technet.microsoft.com/library/dd819476.aspx)和[关于 WS-Management Cmdlet](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets)，或在 Windows PowerShell 控制台中键入 `Get-Help wsman`。

有关更多信息，请参阅：

- [有关远程的常见问题解答](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

有关远程处理错误的帮助，请参阅 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)。

## <a name="see-also"></a>另请参阅

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan 提供程序](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md