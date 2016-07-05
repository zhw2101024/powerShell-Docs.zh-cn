---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "必备条件"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# 必备条件

## 初始状态
在开始此部分内容之前，请确保满足以下条件：

1. JEA 在你的系统上可用。 有关当前支持的操作系统和所需下载，请参阅 [README](./README.md)。
2. 你对用于试用 JEA 的计算机拥有管理权限。
3. 计算机已加入域。
如果你尚未拥有域，请参阅[创建域控制器](#creating-a-domain-controller)部分，以在服务器上快速设置新域。

## 启用 PowerShell 远程处理
通过 PowerShell 远程处理管理 JEA。
在“管理员”PowerShell 窗口中，运行以下命令以确保已启用并已正确配置此项：

```PowerShell
Enable-PSRemoting
```

如果你不熟悉 PowerShell 远程处理，最好运行 `Get-Help about_Remote` 以了解这一重要基本概念。

## 标识你的用户或组
为在操作中展示 JEA，需标识你在本指南中要使用的非管理员用户和组。

如果你使用现有域，请标识或创建一些无特权用户和组。
你将授权这些非管理员访问 JEA。
在脚本顶部看到 `$NonAdministrator` 变量时，请将其分配给所选非管理员用户或组。

如果你从头创建新域，则简单的多。
请参阅附录中的 [设置用户和组](creating-a-domain-controller.md#set-up-users-and-groups) 部分以创建非管理员用户和组。
`$NonAdministrator` 的默认值将为在此部分中创建的组。

## 设置维护角色功能文件
在 PowerShell 中运行以下命令以创建将用于下一部分的演示角色功能文件。
在本指南的稍后部分，你将了解此文件的用途。

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions =
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams
```

## 创建和注册演示会话配置文件
运行以下命令以创建将用于下一部分的演示会话配置文件。
在本指南的稍后部分，你将了解此文件的用途。

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```

## 启用 PowerShell 模块日志记录（可选）
执行以下步骤将为系统上的所有 PowerShell 操作启用日志记录。
并非启用它才能正常使用 JEA，但它在 [报告 JEA](reporting-on-jea.md) 部分中将很有用。

1. 打开本地组策略编辑器
2. 导航至“计算机配置\管理模板\Windows 组件\Windows PowerShell”
3. 双击“打开模块日志记录”
4. 单击“已启用”
5. 在“选项”部分中，单击模块名称旁的“显示”
6. 在弹出窗口中键入“\*”。 这意味着 PowerShell 将记录所有模块的命令。
7. 单击“确定”，应用策略

注意：也可通过“组策略”启用系统范围的 PowerShell 脚本。

**祝贺你！现在你已为计算机配置演示终结点，可以开始使用 JEA 了！**




<!--HONumber=Jun16_HO4-->


