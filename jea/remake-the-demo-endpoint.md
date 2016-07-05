---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "重新创建演示终结点"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: dabb5023012e90ace3fbc5f347c17821abd92595

---

# 重新创建演示终结点
在本部分中，你将了解如何生成上一部分中所使用的演示终结点的精确副本。
这将引入了解 JEA 所必须了解的核心概念，包括 PowerShell 会话配置和角色功能。

## PowerShell 会话配置
在上一部分中使用 JEA 时，你是通过运行以下命令开始的：

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

虽然大多数参数都一目了然，但 *ConfigurationName* 参数最初可能显得令人困惑。
该参数指定了你连接到的 PowerShell 会话配置。

*PowerShell 会话配置*是 PowerShell 终结点的特别术语。
它是一个象征性的“位置”，用户可连接到它并获取 PowerShell 功能的访问权限。
基于会话配置的设置，它可为连接的用户提供不同功能。
对于 JEA，我们使用会话配置将 PowerShell 限制于一组受限的功能，并以具有特权的虚拟帐户身份运行。

你的计算机上已具有多个已注册的 PowerShell 会话配置，其设置各有轻微差异。
其中的大多数是 Windows 自带的，但“JEA_Demo”会话配置是在 [必备条件](prerequisites.md) 部分中设置的。
可在管理员 PowerShell 提示符中运行以下命令以查看所有已注册的会话配置：

```PowerShell
Get-PSSessionConfiguration
```

## PowerShell 会话配置文件
可通过注册新的 *PowerShell 会话配置文件*来创建新的会话配置。
会话配置文件的文件扩展名为“.pssc”。
你可以使用 New-PSSessionConfigurationFile cmdlet 生成会话配置文件。

接下来，你要为 JEA 创建并注册新的会话配置。

## 生成并修改 PowerShell 会话配置
运行以下命令以生成 PowerShell 会话配置“主干”文件。

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **提示：**默认情况下，主干文件仅包含最常用的配置设置。
> 使用 `-Full` 参数以在生成的 PSSC 中包含所有适用设置。

在 PowerShell ISE 或你喜爱的文本编辑器中打开该文件。

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

使用以下值更新文件中的以下字段（请记得在自己的非管理员安全组中进行替换）：

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

以下是各条目的含义：

1.  *SessionType* 字段定义要用于此终结点的预设默认设置。
*RestrictedRemoteServer* 定义远程管理所需的最低设置。
默认情况下，*RestrictedRemoteServer* 终结点将公开 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。
它会将 *ExecutionPolicy* 设置为 *RemoteSigned*，并将 *LanguageMode* 设置为 *NoLanguage*。
这些设置的净效果是用于配置终结点的安全的最低起点。

2.  *RoleDefinitions* 字段将角色功能分配给特定组。
它定义特定用户可以特权帐户身份执行的操作。
使用此字段，你可以指定基于组成员身份的任何连接用户可用的功能。
这是 JEA 的 RBAC 功能的核心。
在此示例中，你将向“Contoso\JEA_NonAdmin_Operator”组的成员公开预制的“演示”角色功能。

3.  *RunAsVirtualAccount* 字段指示 PowerShell 在此终结点处的“运行方式”应为虚拟帐户。
默认情况下，虚拟帐户是内置“管理员”组的成员。
在域控制器上，默认情况下，它也是“域管理员”组的成员。
在本指南稍后部分，你将了解如何自定义虚拟帐户的特权。

4.  *TranscriptDirectory* 字段定义每个远程会话结束后将“即时权限提升”PowerShell 脚本保存到的位置。
这些脚本使你能够以可读的方式检查每个会话中所执行的操作。
有关 PowerShell 脚本的详细信息，请参阅这篇[博客文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。
注意：常规 Windows 事件也将捕获有关每个用户使用 PowerShell 所运行项目的信息。
但脚本可读性稍高。

最后，将你的更改保存到 *JEADemo2.pssc*。

## 应用 PowerShell 会话配置

若要从会话配置文件创建终结点，需注册该文件。
这需要几条信息：

1. 会话配置文件的路径。
2. 你已注册的会话配置的名称。 此名称与用户使用 `Enter-PSSession` 或 `New-PSSession` 连接到你的终结点时向“ConfigurationName”参数提供的名称相同。

若要在本地计算机上注册会话配置，请运行以下命令：

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

祝贺你！ 你已设置 JEA 终结点。

## 测试终结点
针对你的新终结点重新运行 [使用 JEA](using-jea.md) 部分中所列出的步骤，确认它按照预期方式运行。
为 Enter-PSSession 提供配置名称时，请确保使用新的终结点名称 (JEADemo2)。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## 关键概念
**PowerShell 会话配置**：有时称为 *PowerShell 终结点*，这是一个象征性的“位置”，用户可连接到它并获取 PowerShell 功能的访问权限。
你可以通过运行 `Get-PSSessionConfiguration` 列出系统上已注册的会话配置。
以特定方式配置后，可将 PowerShell 会话配置称为 *JEA 终结点*。

**PowerShell 会话配置文件 (.pssc)**：注册后，此文件定义 PowerShell 会话配置的设置。
它包含可连接到终结点的用户角色的规范、“运行方式”虚拟帐户等。     

**角色定义**：会话配置文件中定义授予连接用户的角色功能的字段。
它定义特定*用户*可以特权帐户身份执行的*操作*。
这是 JEA 的 RBAC 功能的核心。

**SessionType**：会话配置文件中表示会话配置的默认设置的字段。
对于 JEA 终结点，必须将此字段设置为 RestrictedRemoteServer。

**PowerShell 脚本**：包含 PowerShell 会话的“即时权限提升”视图的文件。
你可以将 PowerShell 设置为使用 TranscriptDirectory 字段生成 JEA 会话的脚本。
有关脚本的详细信息，请参阅这篇[博客文章](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)。




<!--HONumber=Jun16_HO4-->


