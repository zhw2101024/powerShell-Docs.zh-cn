---
title: 运行远程命令
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# 运行远程命令
你可以使用单个 Windows PowerShell 命令在一台或数百台计算机上运行命令。 Windows PowerShell 通过使用各种技术（包括 WMI、RPC 和 WS-Management）支持远程计算。

## 无需配置即可进行远程处理
许多 Windows PowerShell cmdlet 都具有 ComputerName 参数，此参数可使你在一台或多台远程计算机上收集数据和更改设置。 它们使用各种通信技术，并且许多 cmdlet 在 Windows PowerShell 支持的所有 Windows 操作系统上都有效，而无需任何特殊配置。

这些 cmdlet 包括：

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

通常情况下，支持无需特殊配置即可进行远程处理的 cmdlet 具有 ComputerName 参数，但不具有 Session 参数。 若要在会话中查找这些 cmdlet，请键入：

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Windows PowerShell 远程处理
Windows PowerShell 远程处理，它使用 WS-Management 协议，并且使你可以在一台或多台远程计算机上运行任何 Windows PowerShell 命令。 它使你可以建立持久连接、启动 1:1 交互会话并在多台计算机上运行脚本。

若要使用 Windows PowerShell 远程处理，必须配置远程计算机以进行远程管理。 有关详细信息（包括说明），请参阅 [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)。

配置了 Windows PowerShell 远程处理后，有许多远程处理策略可供你使用。 此文档的其余部分只列出了其中的一部分。 有关详细信息，请参阅 [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) 和 [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)。

### 启动交互会话
若要使用单台远程计算机启动交互会话，请使用 [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) cmdlet。 例如，若要使用 Server01 远程计算器启动交互会话，请键入：

```
enter-pssession Server01
```

命令提示符更改为显示你连接到的计算机的名称。 此后，你在提示符中键入的任何命令都将在远程计算机上运行，并且结果将显示在本地计算机上。

若要结束交互会话，请键入：

```
exit-pssession
```

有关 Enter-PSSession 和 Exit-PSSession cmdlet 的详细信息，请参阅 [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) 和 [Exit-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d)。

### 运行远程命令
若要在一台或多台远程计算机上运行任何命令，请使用 [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462) cmdlet。 例如，若要在 Server01 和 Server02 远程计算机上运行 [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8) 命令，请键入：

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

有关 Invoke-Command cmdlet 的详细信息，请参阅 [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)。

### 运行脚本
若要在一台或多台远程计算机上运行脚本，请使用 Invoke-Command cmdlet 的 FilePath 参数。 该脚本必须在你的本地计算机上或可由其访问。 结果将返回到你的本地计算机。

例如，以下命令在 Server01 和 Server02 远程计算机上运行 DiskCollect.ps1 脚本。

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

有关 Invoke-Command cmdlet 的详细信息，请参阅 [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)。

### 建立持久连接
若要运行一系列共享数据的相关命令，请在远程计算机上创建会话，然后使用 Invoke-Command cmdlet 在你创建的会话中运行命令。 若要创建远程会话，请使用 New-PSSession cmdlet。

例如，以下命令在 Server01 计算机上创建远程会话，在 Server02 计算机上创建另一个远程会话。 它将会话对象保存在 $s 变量中。

```
$s = new-pssession -computername Server01, Server02
```

建立会话后，你可以在这些会话中运行任何命令。 此外，由于会话是持久的，因此你可以在一个命令中收集数据，在后续命令中使用它。

例如，下面的命令在 $s 变量中的会话中运行 Get-Hotfix 命令，并且它将结果保存在 $h 变量中。 将在 $s 中的每个会话中创建 $h 变量，但它不会存在于本地会话中。

```
invoke-command -session $s {$h = get-hotfix}
```

现在，你可以在后续命令中使用 $h 变量中的数据，例如以下命令。 结果将显示在本地计算机上。

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### 高级远程处理
Windows PowerShell 远程管理就在此处开始。 通过使用随 Windows PowerShell 一起安装的 cmdlet，你可以从本地和远程端点建立和配置远程会话、创建自定义和受限制的会话、允许用户从实际在远程会话上隐式运行的远程会话中导入命令、配置远程会话的安全性等。

为了便于远程配置，Windows PowerShell 包含了 WSMan 提供程序。 提供程序创建的 WSMAN: 驱动器使你可以在本地计算机和远程计算机上的配置设置层次结构之间导航。 有关 WSMan 提供程序的详细信息，请参阅 [WSMan 提供程序](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) 和 [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)，或在 Windows PowerShell 控制台中，键入“get-help wsman”。

有关详细信息，请参阅 [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)、[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25) 和 [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)。 有关远程处理错误的帮助，请参阅 [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)。

## 另请参阅
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[WSMan 提供程序](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


