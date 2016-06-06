---
title:  运行远程命令
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---

# 运行远程命令
你可以使用单个 Windows PowerShell 命令在一台或数百台计算机上运行命令。 Windows PowerShell 通过使用各种技术（包括 WMI、RPC 和 WS\-Management）支持远程计算。

## 无需配置即可进行远程处理
许多 Windows PowerShell cmdlet 都具有 ComputerName 参数，此参数可使你在一台或多台远程计算机上收集数据和更改设置。 它们使用各种通信技术，并且许多 cmdlet 在 Windows PowerShell 支持的所有 Windows 操作系统上都有效，而无需任何特殊配置。

这些 cmdlet 包括：

-   [Restart-Computer](https://technet.microsoft.com/en-us/library/dd315301.aspx)

-   [Test-Connection](https://technet.microsoft.com/en-us/library/dd315259.aspx)

-   [Clear-EventLog](https://technet.microsoft.com/en-us/library/dd347552.aspx)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/dd315250.aspx)

-   [Get-Hotfix](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process](https://technet.microsoft.com/en-us/library/dd347630.aspx)

-   [Get-Service](https://technet.microsoft.com/en-us/library/dd347591.aspx)

-   [Set-Service](https://technet.microsoft.com/en-us/library/dd315324.aspx)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/dd315358.aspx)

-   [Get-WmiObject](https://technet.microsoft.com/en-us/library/dd315295.aspx)

通常情况下，支持无需特殊配置即可进行远程处理的 cmdlet 具有 ComputerName 参数，但不具有 Session 参数。 若要在会话中查找这些 cmdlet，请键入：

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Windows PowerShell 远程处理
Windows PowerShell 远程处理使用 WS\-Management 协议，使你可以在一台或多台远程计算机上运行任何 Windows PowerShell 命令。 它使你可以建立持久连接、启动 1:1 交互会话并在多台计算机上运行脚本。

若要使用 Windows PowerShell 远程处理，必须配置远程计算机以进行远程管理。 有关详细信息（包括说明），请参阅[关于远程要求](https://technet.microsoft.com/en-us/library/dd315349.aspx)。

配置了 Windows PowerShell 远程处理后，有许多远程处理策略可供你使用。 此文档的其余部分只列出了其中的一部分。 有关详细信息，请参阅 [About Remote（关于远程）](https://technet.microsoft.com/en-us/library/dd347744.aspx)和 [About Remote FAQ（关于远程 FAQ）](https://technet.microsoft.com/en-us/library/dd347744.aspx)。

### 启动交互会话
若要使用单台远程计算机启动交互会话，请使用 [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet。 例如，若要使用 Server01 远程计算器启动交互会话，请键入：

```
enter-pssession Server01
```

命令提示符更改为显示你连接到的计算机的名称。 此后，你在提示符中键入的任何命令都将在远程计算机上运行，并且结果将显示在本地计算机上。

若要结束交互会话，请键入：

```
exit-pssession
```

有关 Enter\-PSSession 和 Exit\-PSSession cmdlet 的详细信息，请参阅 [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) 和 [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx)。

### 运行远程命令
若要在一台或多台远程计算机上运行任何命令，请使用 [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet。
例如，若要在 Server01 和 Server02 远程计算机上运行 [Get-UICulture ](https://technet.microsoft.com/en-us/library/dd347742.aspx) 命令，请键入：

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

输出将返回到你的计算机。

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

有关 Invoke\-Command cmdlet 的详细信息，请参阅 [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)。

### 运行脚本
若要在一台或多台远程计算机上运行脚本，请使用 Invoke\-Command cmdlet 的 FilePath 参数。 该脚本必须在你的本地计算机上或可由其访问。 结果将返回到你的本地计算机。

例如，以下命令在 Server01 和 Server02 远程计算机上运行 DiskCollect.ps1 脚本。

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

有关 Invoke\-Command cmdlet 的详细信息，请参阅 [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx)。

### 建立持久连接
若要运行一系列共享数据的相关命令，请在远程计算机上创建会话，然后使用 Invoke\-Command cmdlet 在你创建的会话中运行命令。 若要创建远程会话，请使用 New\-PSSession cmdlet。

例如，以下命令在 Server01 计算机上创建远程会话，在 Server02 计算机上创建另一个远程会话。 它将会话对象保存在 $s 变量中。

```
$s = new-pssession -computername Server01, Server02
```

建立会话后，你可以在这些会话中运行任何命令。 此外，由于会话是持久的，因此你可以在一个命令中收集数据，在后续命令中使用它。

例如，下面的命令可在 $s 变量中的会话中运行 Get\-Hotfix 命令，然后将结果保存在 $h 变量中。 将在 $s 中的每个会话中创建 $h 变量，但它不会存在于本地会话中。

```
invoke-command -session $s {$h = get-hotfix}
```

现在，你可以在后续命令中使用 $h 变量中的数据，例如以下命令。 结果将显示在本地计算机上。

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"} }
```

### 高级远程处理
Windows PowerShell 远程管理就在此处开始。 通过使用随 Windows PowerShell 一起安装的 cmdlet，你可以从本地和远程端点建立和配置远程会话、创建自定义和受限制的会话、允许用户从实际在远程会话上隐式运行的远程会话中导入命令、配置远程会话的安全性等。

为了便于远程配置，Windows PowerShell 包含了 WSMan 提供程序。 提供程序创建的 WSMAN: 驱动器使你可以在本地计算机和远程计算机上的配置设置层次结构之间导航。
有关 WSMan 提供程序的详细信息，请参阅 [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) 和   [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx)（关于 WS-Management Cmdlet），或在 Windows PowerShell 控制台中键入“get\-help wsman”。

有关更多信息，请参阅：
- [关于远程 FAQ](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx)。 

有关远程处理错误的帮助，请参阅 [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx)。

## 另请参阅
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [New-PSSession](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [WSMan 提供程序](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=May16_HO4-->


