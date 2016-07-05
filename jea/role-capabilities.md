---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "角色功能"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 5b6dcb205d2c3cbb1a98c6465cb1002b9ed61459

---

# 角色功能

## 概述
在上一部分中，你已了解到“RoleDefinitions”字段定义有权访问各角色功能的组。
你可能想问，“什么是角色功能？”
本部分将回答这个问题。  

## PowerShell 角色功能简介
PowerShell 角色功能定义用户可在 JEA 终结点执行的“操作”。
它们详细介绍了可见命令、可见应用程序等内容的白名单。
角色功能由扩展名为“.psrc”的文件定义。

## 角色功能内容
我们首先将检查并修改你之前使用的演示角色功能文件。
假设你在环境中部署了会话配置，但收到反馈称需要更改向用户公开的功能。
操作员需要能够重启计算机，并且他们还希望能够获取有关网络设置的信息。
此外，安全团队告知你不加任何限制而允许用户运行“Restart-Service”是不可接受的。
你需要限制操作员能重启的服务。

若要进行这些更改，请首先以管理员身份运行 PowerShell ISE 并打开以下文件：

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

现在找到并更新文件中的以下行：

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

这包含几个有趣的示例：

1.  你已限制了 Restart-Service，使操作员仅可运行带有 -Name 参数的 Restart-Service，并且仅允许其将“Spooler”作为实参提供给形参。
如果愿意，你还可以使用使用“ValidatePattern”而不是“ValidateSet”的正则表达式来限制参数。

2.  你公开了 NetTCPIP 模块中带有“Get”谓词的所有命令。
因为“Get”命令通常不会更改系统状态，所以此操作相对安全。
也就是说，强烈推荐仔细检查通过 JEA 公开的每个命令。

3.  你使用 VisibleExternalCommands 公开了可执行文件 (ipconfig)。
也可使用此字段公开完整的 PowerShell 脚本。
请务必提供外部命令的完整路径，以避免执行了位于用户路径中的同名（潜在恶意）程序。

保存该文件，然后再次连接到演示终结点以确认更改生效。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
由于你仅修改了角色功能文件，因此无需重新注册会话配置。
当用户连接时，PowerShell 将自动查找更新的角色功能。
由于角色功能在会话启动时加载，因此现有会话不受角色功能文件更新的影响。

现在，请通过运行带有 -WhatIf 参数的 Restart-Computer 确认你可以重启计算机（除非你确实想重启计算机）。

```PowerShell
Restart-Computer -WhatIf
```

确认你可以运行“ipconfig”

```PowerShell
ipconfig
```

最后，确认 Restart-Service 仅适用于后台处理程序服务。

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail
```

完成后退出会话。

```PowerShell
Exit-PSSession
```

## 角色功能创建
在下一部分中，你将为 AD 技术支持用户创建 JEA 终结点。
我们将首先创建空白的角色配置文件，准备在该部分中进行填充。
为了在会话启动时解析角色功能，必须在有效 PowerShell 模块内的“RoleCapabilities”文件夹中创建它。

PowerShell 模块实际上是 PowerShell 功能的包。
它们可以包含 PowerShell 函数、cmdlet、DSC 资源、角色功能等。
你可以通过在 PowerShell 控制台中运行 `Get-Help about_Modules` 来查找有关模块的信息。

若要创建带有空白的角色功能文件的新 PowerShell 模块，请运行以下命令：  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

祝贺你！你已创建空白角色功能文件。
将在下一部分中使用它。

## 关键概念
**角色功能 (.psrc)**：定义用户可在 JEA 终结点执行的“操作”的文件。
它详细介绍了可见命令、可见控制台应用程序等内容的白名单。
为使 PowerShell 能检测角色功能，必须将其置于有效 PowerShell 模块内的“RoleCapabilities”文件夹中。

**PowerShell 模块**：PowerShell 功能的包。
它可以包含 PowerShell 函数、cmdlet、DSC 资源、角色功能等。
为实现自动加载，PowerShell 模块必须位于 `$env:PSModulePath` 中的路径下。




<!--HONumber=Jun16_HO4-->


