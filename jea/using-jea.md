---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "使用 jea"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 88ce340c09efdbb3d81a72fe6113c1187a9152f2
ms.openlocfilehash: 9db7a5a91d25d459313117da34af63016f03c241

---

# 使用 JEA
本部分的重点在于了解*使用 JEA* 的最终用户体验。
在必备条件部分中，你创建了一个演示 JEA 终结点。
我们将使用此演示在操作中展示 JEA。
在稍后的部分中，本指南将逆向操作 -- 介绍赖以实现这种最终用户体验的操作和文件。

## 以非管理员身份使用 JEA
要在操作中展示 JEA，需以非管理员用户身份使用 PowerShell 远程处理。
在新 PowerShell 窗口中运行以下命令：   

```PowerShell
$NonAdminCred = Get-Credential
```

根据提示输入非管理员帐户的凭据。
如果你按照[设置用户和组](creating-a-domain-controller.md#set-up-users-and-groups)部分进行操作，则凭据如下：
-   用户名 =“OperatorUser”
-   密码 =“pa$ $w0rd”

接下来，运行以下命令以使用你提供的凭据连接到演示终结点：

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

你现已在本地计算机上进入交互式远程 PowerShell 会话。
使用“Credential”参数，你以 OperatorUser（或你所使用的任何帐户）*身份*进行了连接。
提示中对 `[localhost]: PS>` 的更改指示你正在针对远程会话进行操作。  

在远程命令提示符中运行以下命令，以显示可用的命令：

```PowerShell
Get-Command
```

显而易见，这是正常 PowerShell 窗口中可用命令的一个及其有限的子集（正常窗口中通常可以包括数千条命令）。
具体而言，它仅显示了 8 个默认 JEA 命令（Clear-Host、Exit-PSSession、Get-Command、Get-FormatData、Get-Help、Measure-Object、Out-Default、Select-Object）和维护角色功能文件中显式包含的 2 个命令。

接下来，让我们通过调用维护角色功能文件中包含的自定义函数，查看此会话运行于的用户上下文：

```PowerShell
Get-UserInfo
```

此函数的输出显示“ConnectedUser”和“RunAsUser”。
连接的用户即连接到远程会话的帐户（例如你的帐户）。
连接的用户不必具有管理员特权。
“运行方式”帐户是实际执行特权操作的帐户。
通过以某一用户身份连接并以某一特权的用户身份运行，我们使非特权用户能够执行特定的管理任务，而无需授予其管理权限。

若要在操作中对此进行演示，请运行以下命令：

```PowerShell
Restart-Service -Name Spooler -Verbose
```

正常情况下，需要管理员特权才能运行 Restart-Service。
但是凭借 JEA 虚拟帐户，我们能够使用非特权凭据运行它。

因此，JEA 使你能够使用你所使用的命令来完成作业。
但是，*不应*允许你使用的命令呢？
尝试在 JEA 会话中运行其他命令（如 `Restart-Computer`），注意 JEA 将阻止执行此类命令。

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

最后，为离开受约束的 JEA 终结点，请运行以下命令：

```PowerShell
Exit-PSSession
```

这会使你从远程 PowerShell 会话断开连接。




<!--HONumber=Jul16_HO1-->


