---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "端到端 - Active Directory"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0a262e2c83174db7041d3cf35d97542b1cac4386

---

# 端到端 - Active Directory
假设你的程序作用域扩大了。
你现在有责任将 JEA 添加到域控制器以执行 Active Directory 操作。
技术支持人员将使用 JEA 解锁帐户、重置密码以及执行其他类似操作。

你需要向另一组人员公开全新的一组命令。
在此基础上，你还需公开一组现有 Active Directory 脚本。
本部分将演练为此任务创作会话配置和角色功能。

## 必备条件
若要按照此部分进行逐步操作，需在域控制器上进行操作。
如果你无权访问你的域控制器，请不要担心。
请尝试对你熟悉的其他方案或角色进行操作以便跟进。
如果你想要快速设置新的域控制器，请参阅[“创建域控制器”附录](#creating-a-domain-controller)。

## 创建新角色功能和会话配置的步骤

创建新角色功能乍看令人生畏，但可将其分为相当简单的几个步骤：

1.  确定需要启用的任务
2.  根据需要限制这些任务
3.  确认它们适用于 JEA
4.  将其置于角色功能文件中
5.  注册用于公开该角色功能的会话配置

## 步骤 1：确定需要公开的内容
在创建新角色功能或会话配置之前，需要确定用户需通过 JEA 终结点执行的所有操作，以及如何通过 PowerShell 来执行这些操作。
这将涉及大量的需求收集和研究。
你进行此过程的方式将取决于你的组织和目标。
请务必将需求收集和研究作为实际过程的一个关键部分。
这可能是采用 JEA 的过程中最艰难的步骤。

### 查找资源
针对创建 Active Directory 管理终结点进行研究时，你可能找到了以下一组在线资源：
-   [Active Directory PowerShell 概述](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [适用于 Active Directory 的 CMD 到 PowerShell 指南](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### 制作列表
在本节剩余部分中，你将进行以下十个操作。
请注意这只是一个示例，你组织的需求可能会有所不同：

|操作                                                         |PowerShell 命令                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|帐户解锁                                                 |`Unlock-ADAccount`                                             |
|密码重置                                                 |`Set-ADAccountPassword` 和 `Set-ADUser -ChangePasswordAtLogon`|
|更改用户的职务                                          |`Set-ADUser -Title`                                            |  
|查找处于已锁定、已禁用、已停用等状态的 AD 帐户 |`Search-ADAccount`                                             |
|将用户添加到组                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|从组中删除用户                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|启用用户帐户                                          |`Enable-ADAccount`                                             |
|禁用用户帐户                                         |`Disable-ADAccount`                                            |

## 步骤 2：根据需要限制任务

现在你拥有了操作的列表，需仔细思考每个命令的功能。
这样做有两个重要的原因：

1.  首先，容易公开使用户具有比你预期的更多功能。
例如，`Set-ADUser` 是一个极其强大和灵活的命令。
你可能不希望向技术支持用户公开其全部功能。  

2.  更糟糕的是，它可能会公开允许用户脱离 JEA 限制的命令。
如果发生这种情况，JEA 将不再起到安全边界的作用。
请谨慎选择命令。
例如，Invoke-Expression 将允许用户运行不受限制的代码。
有关这一主题的详细讨论，请参阅“限制命令时的注意事项”部分。

检查每个命令后，请决定限制以下内容：

1.  `Set-ADUser` 应仅允许在使用“-Title”参数时运行

2.  `Add-ADGroupMember` `Remove-ADGroupMember` 应仅适用于特定组

### 步骤 3：确认任务适用 JEA
在受限的 JEA 环境中，实际使用这些 cmdlet 可能并不直接。
JEA 在*无语言*模式下运行，该模式（以及其他一些模式）将阻止用户使用变量。
为确保最终用户具有流畅的体验，请务必检查某些内容。

例如，请考虑 `Set-ADAccountPassword`。
“-NewPassword”参数需要安全字符串。
用户常创建安全字符串并将其作为变量进行传递（如下所示）：

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

但是，无语言模式阻止使用变量。
你可以通过两种方式避开此限制：

1.  你可以要求用户运行命令而不分配变量。
这很容易配置，但可能令操作员苦于使用终结点。
谁愿意每次重置密码时都键入安全字符串？
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  你可以在向最终用户公开的脚本或函数中包装复杂性。
你公开的脚本和函数在不受限制的上下文中运行；你可以编写使用变量的函数并调用其他命令而不会引发任何问题。
这种方法可简化最终用户体验、避免错误、减少所需 PowerShell 知识，并减少过多功能的无意公开。
唯一的缺点是创作和维护函数的成本。

### 保留：将函数添加到模块
采用方法 2，你将编写名为 `Reset-ContosoUserPassword` 的 PowerShell 函数。
当你重置用户密码时，此函数将执行所需的一切操作。
在你的组织中，这可能涉及到特别而复杂的操作。
因为这只是一个示例，因此你的命令将仅重置密码并要求用户在登录时更改密码。
我们会将它放在你在最后一部分中创建的 Contoso_AD_Module 模块中。

1. 在 PowerShell ISE 中，打开“Contoso_AD_Module.psm1”
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. 按 Crtl+J 以打开代码片段菜单。

3. 按着下箭头键直到你找到“function”，然后按 Enter。
这将显示函数最基本的主干。

4. 将函数重命名为“Reset-ContosoUserPassword”。  

5. 将参数之一重命名为“Identity”，并删除另一参数。

6. 将以下内容复制到该函数的正文。
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. 保存该文件。
最后，你应该得到如下所示的内容：
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
现在，你的用户可以轻松调用 `Reset-ContosoUserPassword` 而无需记忆创建安全字符串内联的语法。

## 步骤 4：编辑角色功能文件
在[角色功能创建](#role-capability-creation)部分，你创建了一个空白的角色功能文件。
在本部分中，你将在该文件中填充值。

首先在 ISE 中打开该角色功能文件。
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
使用以下更改更新文件：
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

有关上述部分，需要注意以下几点：
1.  PowerShell 将尝试自动加载你的角色功能所需的模块。
如果你注意到未自动加载模块的问题，可能需要在“ModulesToImport”字段中显式列出模块名称。

2.  如果你不确定某命令是 cmdlet 还是函数，请运行 `Get-Command` 并查看“CommandType”

3.  如果不易定义一组允许的值，可通过 ValidatePattern 使用正则表达式来限制形参实参。
不能为单个参数同时定义 ValidatePattern 和 ValidateSet。

## 步骤 5：注册新会话配置
接下来，你将创建新的会话配置文件，该文件将向“JEA_NonAdmin_HelpDesk”AD 组的成员公开你的角色功能。

首先在 PowerShell ISE 中创建并打开新的空白会话配置文件。
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
修改 PSSC 文件中的以下字段。
如果你正在自己的环境中工作，应将“CONTOSO\JEA_NonAdmins_Helpdesk”替换为你自己的非管理员用户或组。
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
保存并注册会话配置
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## 动手检验吧！
获取你的非管理员用户凭据：
```PowerShell
$HelpDeskCred = Get-Credential
```
如果按照 [设置用户和组](creating-a-domain-controller.md#set-up-users-and-groups) 部分进行操作，则凭据如下：
-   用户名 =“HelpDeskUser”
-   密码 =“pa$ $w0rd”

使用非管理员凭据远程登录到 AD 支持人员终结点：
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
使用 Set-ADUser 重置用户的职务。
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
验证职务是否已更改。
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
现在，使用 Add-ADGroupMember 将用户添加到 TestGroup。
注意：请确保事先创建了 TestGroup。
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
退出会话：
```PowerShell
Exit-PSSession
```
## 关键概念
**NoLanguage 模式**：当 PowerShell 处于“NoLanguage”模式时，用户仅能运行命令，而不能使用任何语言元素。
有关详细信息，请运行 `Get-Help about_Language_Modes`。

**PowerShell 函数**：PowerShell 函数是可以按名称调用的小型 PowerShell 代码。
有关详细信息，请运行 `Get-Help about_Functions`。

**ValidateSet/ValidatePattern**：公开命令时，你可以限制特定形参的有效实参。
ValidateSet 是有效命令的特定列表。
ValidatePattern 是该形参的实参必须匹配的正则表达式。




<!--HONumber=Jun16_HO4-->


