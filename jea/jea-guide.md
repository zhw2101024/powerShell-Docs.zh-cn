# Just Enough Administration (JEA)：简介

## 目录
阅读本文档后，你应该能创作、部署、使用、维护和审核 Just Enough Administration (JEA) 部署。
以下是本介绍指南中所涵盖的主题：

1.  [简介](#introduction)：简要了解为何应关心 JEA

2.  [必备条件](#prerequisites)：设置你的环境

3.  [使用 JEA](#using-jea)：从了解使用 JEA 的操作员体验开始

4.  [重新创建演示](#remake-the-demo-endpoint)：从头开始创建 JEA 会话配置

5.  [角色功能](#role-capabilities)：了解如何使用角色功能文件自定义 JEA 功能

6.  [端到端 - Active Directory](#end-to-end---active-directory)：创建用于管理 Active Directory 的全新的终结点

7.  [多计算机部署和维护](#multi-machine-deployment-and-maintenance)：了解部署和创作如何随扩展而更改

8.  [报告 JEA](#reporting-on-jea)：了解如何审核和报告所有 JEA 操作和基础结构

9.  [附录](#appendix)：重要技能和讨论点

## 简介

### 动机
当对某人授予你系统的特许访问权时，即将信任边界扩展至此人。
这会带来风险 -- 管理员会成为受攻击面。
内部攻击和凭据盗窃真实存在并且很常见。

这并不是个新问题。
你可能非常熟悉最小特权的原则，并将某种形式的基于角色的访问控制 (RBAC) 用于提供最小特权的应用程序。
但是，这些解决方案的有效性和可管理性常受限于其广泛性和不精确性。
此外，RBAC 作用范围中存在缺口。
例如，在 Windows 中，特许访问权很大程度上是一个二进制开关，在将用户添加到“管理员”组时会强制你授予其不必要的权限。

Just Enough Administration (JEA) 通过 PowerShell 远程处理提供 RBAC 平台。
*它允许特定用户在服务器上执行特定管理任务，而不授予其管理员权限。*
这让你能够填补现有 RBAC 解决方案之间的缺口，并简化了这些设置的管理。

## 必备条件

### 初始状态
在开始此部分内容之前，请确保满足以下条件：

1. JEA 在你的系统上可用。 有关当前支持的操作系统和所需下载，请参阅 [README](./README.md)。
2. 你对用于试用 JEA 的计算机拥有管理权限。
3. 计算机已加入域。
如果你尚未拥有域，请参阅[创建域控制器](#creating-a-domain-controller)部分，以在服务器上快速设置新域。

### 启用 PowerShell 远程处理
通过 PowerShell 远程处理管理 JEA。
在“管理员”PowerShell 窗口中，运行以下命令以确保已启用并已正确配置此项：

```PowerShell
Enable-PSRemoting 
```

如果你不熟悉 PowerShell 远程处理，最好运行 `Get-Help about_Remote` 以了解这一重要基本概念。

### 标识你的用户或组
为在操作中展示 JEA，需标识你在本指南中要使用的非管理员用户和组。
  
如果你使用现有域，请标识或创建一些无特权用户和组。
你将授权这些非管理员访问 JEA。
在脚本顶部看到 `$NonAdministrator` 变量时，请将其分配给所选非管理员用户或组。 

如果你从头创建新域，则简单的多。
请参阅附录中的[设置用户和组](#set-up-users-and-groups)部分，创建非管理员用户和组。
`$NonAdministrator` 的默认值将为在此部分中创建的组。

### 设置维护角色功能文件
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
  
### 创建和注册演示会话配置文件
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
 
### 启用 PowerShell 模块日志记录（可选）
执行以下步骤将为系统上的所有 PowerShell 操作启用日志记录。
并非启用它才能正常使用 JEA，但它在[报告 JEA](#reporting-on-jea) 部分中将很有用。

1. 打开本地组策略编辑器
2. 导航至“计算机配置\管理模板\Windows 组件\Windows PowerShell”
3. 双击“打开模块日志记录”
4. 单击“已启用”
5. 在“选项”部分中，单击模块名称旁的“显示”
6. 在弹出窗口中键入“*”。 这意味着 PowerShell 将记录所有模块的命令。
7. 单击“确定”，应用策略

注意：也可通过“组策略”启用系统范围的 PowerShell 脚本。

**祝贺你！现在你已为计算机配置演示终结点，可以开始使用 JEA 了！**

## 使用 JEA
本部分的重点在于了解*使用 JEA* 的最终用户体验。
在必备条件部分中，你创建了一个演示 JEA 终结点。
我们将使用此演示在操作中展示 JEA。
在稍后的部分中，本指南将逆向操作 -- 介绍赖以实现这种最终用户体验的操作和文件。

### 以非管理员身份使用 JEA
要在操作中展示 JEA，需以非管理员用户身份使用 PowerShell 远程处理。
在新 PowerShell 窗口中运行以下命令：   

```PowerShell
$NonAdminCred = Get-Credential
```

根据提示输入非管理员帐户的凭据。
如果你按照[设置用户和组](#set-up-users-and-groups)部分进行操作，则凭据如下：
-   用户名 =“OperatorUser”
-   密码 =“pa$ $w0rd”

接下来，运行以下命令以使用你提供的凭据连接到演示终结点：

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

你现已在本地计算机上进入交互式远程 PowerShell 会话。 使用“Credential”参数，你以 OperatorUser（或你所使用的任何帐户）*身份*进行了连接。
提示中对 `[localhost]: PS>` 的更改指示你正在针对远程会话进行操作。  

在远程命令提示符中运行以下命令，以显示可用的命令：

```PowerShell
Get-Command 
```

显而易见，这是正常 PowerShell 窗口中可用命令的一个及其有限的子集（正常窗口中通常可以包括数千条命令）。
具体而言，它仅显示了 7 个默认 JEA cmdlet（Clear-Host、Exit-PSSession、Get-Command、Get-FormatData、Get-Help、Measure-Object、Out-Default、Select-Object）和维护角色功能文件中显式包含的 2 个命令。

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

## 重新创建演示终结点
在本部分中，你将了解如何生成上一部分中所使用的演示终结点的精确副本。
这将引入了解 JEA 所必须了解的核心概念，包括 PowerShell 会话配置和角色功能。 

### PowerShell 会话配置
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
其中的大多数是 Windows 自带的，但“JEA_Demo”会话配置是在[必备条件](#prerequisites)部分中设置的。
可在管理员 PowerShell 提示符中运行以下命令以查看所有已注册的会话配置：

```PowerShell
Get-PSSessionConfiguration
```

### PowerShell 会话配置文件
可通过注册新的 *PowerShell 会话配置文件*来创建新的会话配置。
会话配置文件的文件扩展名为“.pssc”。
你可以使用 New-PSSessionConfigurationFile cmdlet 生成会话配置文件。

接下来，你要为 JEA 创建并注册新的会话配置。 

### 生成并修改 PowerShell 会话配置
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
*RestrictedRemoteServer* 定义远程管理所需的最低设置。 默认情况下，*RestrictedRemoteServer* 终结点将公开 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。
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

### 应用 PowerShell 会话配置 

若要从会话配置文件创建终结点，需注册该文件。
这需要几条信息：

1. 会话配置文件的路径。
2. 你已注册的会话配置的名称。 此名称与用户使用 `Enter-PSSession` 或 `New-PSSession` 连接到你的终结点时向“ConfigurationName”参数提供的名称相同。

若要在本地计算机上注册会话配置，请运行以下命令：

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

祝贺你！ 你已设置 JEA 终结点。

### 测试终结点
针对你的新终结点重新运行[使用 JEA](#using-jea) 部分中所列出的步骤，确认它按照预期方式运行。
为 Enter-PSSession 提供配置名称时，请确保使用新的终结点名称 (JEADemo2)。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### 关键概念
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

## 角色功能

### 概述
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

### 角色功能创建
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

### 关键概念
**角色功能 (.psrc)**：定义用户可在 JEA 终结点执行的“操作”的文件。
它详细介绍了可见命令、可见控制台应用程序等内容的白名单。
为使 PowerShell 能检测角色功能，必须将其置于有效 PowerShell 模块内的“RoleCapabilities”文件夹中。

**PowerShell 模块**：PowerShell 功能的包。
它可以包含 PowerShell 函数、cmdlet、DSC 资源、角色功能等。
为实现自动加载，PowerShell 模块必须位于 `$env:PSModulePath` 中的路径下。 

## 端到端 - Active Directory
假设你的程序作用域扩大了。
你现在有责任将 JEA 添加到域控制器以执行 Active Directory 操作。
技术支持人员将使用 JEA 解锁帐户、重置密码以及执行其他类似操作。

你需要向另一组人员公开全新的一组命令。
在此基础上，你还需公开一组现有 Active Directory 脚本。
本部分将演练为此任务创作会话配置和角色功能。

### 必备条件
若要按照此部分进行逐步操作，需在域控制器上进行操作。
如果你无权访问你的域控制器，请不要担心。
请尝试对你熟悉的其他方案或角色进行操作以便跟进。
如果你想要快速设置新的域控制器，请参阅[“创建域控制器”附录](#creating-a-domain-controller)。

### 创建新角色功能和会话配置的步骤

创建新角色功能乍看令人生畏，但可将其分为相当简单的几个步骤：

1.  确定需要启用的任务
2.  根据需要限制这些任务
3.  确认它们适用于 JEA
4.  将其置于角色功能文件中
5.  注册用于公开该角色功能的会话配置

### 步骤 1：确定需要公开的内容
在创建新角色功能或会话配置之前，需要确定用户需通过 JEA 终结点执行的所有操作，以及如何通过 PowerShell 来执行这些操作。
这将涉及大量的需求收集和研究。
你进行此过程的方式将取决于你的组织和目标。
请务必将需求收集和研究作为实际过程的一个关键部分。
这可能是采用 JEA 的过程中最艰难的步骤。

#### 查找资源
针对创建 Active Directory 管理终结点进行研究时，你可能找到了以下一组在线资源：
-   [Active Directory PowerShell 概述](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [适用于 Active Directory 的 CMD 到 PowerShell 指南](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### 制作列表
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

### 步骤 2：根据需要限制任务

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

#### 保留：将函数添加到模块
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

### 步骤 4：编辑角色功能文件
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

### 步骤 5：注册新会话配置
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
### 动手检验吧！
获取你的非管理员用户凭据：
```PowerShell
$HelpDeskCred = Get-Credential
```
如果你按照设置用户和组部分进行操作，则凭据如下：
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
### 关键概念
**NoLanguage 模式**：当 PowerShell 处于“NoLanguage”模式时，用户仅能运行命令，而不能使用任何语言元素。
有关详细信息，请运行 `Get-Help about_Language_Modes`。

**PowerShell 函数**：PowerShell 函数是可以按名称调用的小型 PowerShell 代码。
有关详细信息，请运行 `Get-Help about_Functions`。

**ValidateSet/ValidatePattern**：公开命令时，你可以限制特定形参的有效实参。
ValidateSet 是有效命令的特定列表。
ValidatePattern 是该形参的实参必须匹配的正则表达式。

## 多计算机部署和维护
此时，你已多次将 JEA 部署到本地系统。
因为你的生产环境可能由多台计算机组成，因此请务必演练部署过程中必须在每台计算机上重复的关键步骤。

### 大致步骤：
1.  将你的模块（及角色功能）复制到每个节点。
2.  将你的会话配置文件复制到每个节点。
3.  使用你的会话配置运行 `Register-PSSessionConfiguration`。
4.  在安全的位置保留会话配置和工具包的一份副本。
进行修改时，最好拥有“单一事实来源”。

### 示例脚本
以下是部署的一个示例脚本。
若要在你的环境中使用它，需使用实际文件共享和模块的名称/路径。
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### 修改功能
当处理多台计算机时，请务必以一致的方式推行修改。
JEA 拥有 DSC 资源时，这将帮助确保你的环境保持同步。
在此之前，我们强烈建议你保留会话配置的主副本，并在每次修改后进行重新部署。

### 删除功能
若要从系统中删除 JEA 配置，请在每台计算机上使用以下命令：
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## JEA 报告
因为 JEA 允许非特权用户在特权上下文中运行，所以日志记录和审核尤为重要。
在本节中，我们将逐一运行可用于帮助进行行日志记录和报告的工具。

### 报告 JEA 操作
#### 即时权限提升脚本
获取在 PowerShell 会话中所发生情况的摘要最快捷的方法之一，是通过即时权限提升查看进行键入的用户。
查看其命令、这些命令的输出是否一切正常。
或者并非一切正常，但至少你了解情况。
PowerShell 脚本旨在出现问题后，给予你类似的视图。

在会话配置中使用“TranscriptDirectory”字段时，PowerShell 将自动记录给定会话中执行的所有操作的脚本。
可在以下位置找到你执行本文档中的会话所生成的脚本：“$env:ProgramData\JEAConfiguration\Transcripts”

显而易见，该脚本记录了有关“已连接的”用户、“运行方式”用户、会话中运行的命令等的信息。
有关 PowerShell 脚本的详细信息，请参阅这篇[博客文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。

#### PowerShell 事件日志
在模块日志记录处于打开状态时，所有的 PowerShell 操作也会记录在常规的 Windows 事件日志中。
与脚本相比，处理这种日志稍显复杂，但是它提供的详细信息级别可能有用。

在“PowerShell”运行日志中，如果你启用了模块日志记录，事件 ID 4104 将记录调用的每个命令。

#### 其他事件日志
与 PowerShell 日志和脚本不同，其他日志记录机制将不会捕获“已连接的用户”。
你需要在其他日志和 PowerShell 日志之间进行一些关联操作，以匹配所执行的操作。

在“Windows 远程管理”运行日志中，事件 ID 193 将记录连接用户的 SID 和名称，以及运行方式虚拟帐户的 SID，来帮助进行此关联。
你可能也注意到了运行方式虚拟帐户末尾包含连接用户的域和用户名。

### 报告 JEA 配置
#### Get-PSSessionConfiguration
为了准确报告你的环境状态，了解在计算机上设置的 JEA 终结点数量很重要。
`Get-PSSessionConfiguration` 请务必了解此信息。
 
#### Get-PSSessionCapability
通过 JEA 终结点手动报告任意给定用户的功能可能相当复杂。
你可能需要检查多个角色功能。
幸运的是，“Get-PSSessionCapability”cmdlet 可完成此操作。

若要进行验证，请从管理员 PowerShell 提示符运行以下命令：
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## 结论 
完成本指南之后，你应该拥有用于创建你自己的 JEA 终结点的工具和词汇。 感谢阅读！

## 附录

## 本指南中使用的主要概念
**PowerShell 远程处理**：通过 PowerShell 远程处理，你可以针对远程计算机运行 PowerShell 命令。
你可以针对一台或多台计算机进行操作，并可使用临时或永久连接。
在此演示中，你使用交互式会话远程到本地计算机。
JEA 通过 PowerShell 远程处理限制可用的功能。
有关 PowerShell 远程处理的详细信息，请运行 `Get-Help about_Remote`。

**“运行方式”用户**：使用 JEA 时，非管理员的“运行方式”有为特权的“虚拟帐户”。
虚拟帐户仅在远程会话期间存在。
也就是说，用户连接到终结点时创建此用户，用户结束会话时销毁它。
默认情况下，虚拟帐户是本地“管理员”组的成员。
在域控制器上，它是“域管理员”组的成员。
虚拟帐户对于在其上创建这些帐户的计算机来说是本地的，并且不拥有该计算机之外的权限。
这意味着它们没有在 Active Directory 中进行注册（未分配 RID）。
此外，如果允许的命令/脚本尝试访问本地计算机外部的资源，它将在计算机标识（而不是虚拟帐户标识）下访问这些资源。

**“已连接的”用户**：连接到 JEA 终结点并向其分配了角色的非管理员用户。
此用户运行的任何命令都在运行方式用户或虚拟帐户的上下文之下运行。


### 创建域控制器

本文档假定你的计算机已加入域。
如果你当前尚未加入域，这一部分可以帮助你使用 DSC 快速建立起域控制器。

#### 必备条件

1.  计算机位于内部网络上
2.  计算机未加入到现有域
3.  计算机正在运行 Windows Server 2016 或安装了 WMF 5.0

#### 安装 xActiveDirectory
如果你的计算机具有有效的 Internet 连接，请在提升的 PowerShell 窗口中输入以下命令：
```PowerShell
Install-Module xActiveDirectory -Force 
```
如果没有 Internet 连接，请将 xActiveDirectory 安装到另一台计算机，然后将 xActiveDirectory 文件夹复制到你的计算机上的“C:\Program Files\WindowsPowerShell\Modules”文件夹。

若要确认安装成功，请运行以下命令：
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### 使用 DSC 设置域
将以下脚本复制到 PowerShell 中，使你的计算机成为新域中的域控制器。
**作者注释：不使用提供的凭据将导致已知问题。  为了安全起见，请勿忘记你的本地管理员密码。**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
你的计算机将重启数次。
看到包含“Domain has been created.”的名为“C:\temp.txt”的文件，表示过程已完成。 

#### 设置用户和组
以下命令将在你的域中设置“操作员和技术支持人员”组以及身为该组成员的相应非管理员用户。
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### 关于列入黑名单
在体验了一番 JEA 后，你可能会想知道是否可以将命令列入黑名单。
这一请求可以理解，但由于以下原因，目前未计划为 JEA 提供此功能：

1.  我们对 JEA 的设计是，将操作员限制为仅能执行其所需执行的操作。
黑名单则相反。

2.  PowerShell 命令的作者在设计 PowerShell 时未考虑 JEA。
在全新安装的 Windows Server 2016 上，有大约 1520 条命令立即可用。
这些命令的威胁模型未包括这种可能性，即用户将以更高权限的帐户身份运行命令。
例如，某些命令允许通过设计注入代码（例如核心 PowerShell 模块中的 Add-Type 和 Invoke-Command）。
JEA 在你公开已知特定命令时可发出警告，但是我们尚未根据新的威胁模型重新评估 Windows 中的每条命令。
请务必了解你通过 JEA 公开的命令的功能。  

3.  此外，即使 JEA 阻止了具有代码注入漏洞的所有命令，也不能保证恶意用户不能使用其他相关命令执行已列入黑名单的操作。
如果你不了解你公开的所有命令，你将无法保证某些操作是不可能的。
你肩负了解你所公开的命令的重任，无论这些命令使用白名单还是黑名单。
无法管理黑名单将公开的命令数量，因此改用白名单实现 JEA。

### 限制命令时的注意事项
执行此步骤时有一个重点。
将通过 JEA 公开的所有功能置于仅限管理员的区域，这至关重要。
非管理员用户应不能修改通过 JEA 终结点使用的脚本。

关于这一点请注意，切勿允许 JEA 用户覆盖 JEA 配置和其 JEA 会话中已列入白名单的脚本。
公开 `Copy-Item` 等命令时请格外小心！

### 角色功能的常见问题
你自己完成此过程时，可能遇到一些常见问题。
以下是一个快速指南，阐释了修改或创建新的终结点时如何确定并修正这些问题：

#### 函数与Cmdlet
在 PowerShell 中编写的 PowerShell 命令即 PowerShell 函数。
作为为专用 .NET 类编写的 PowerShell 命令即 PowerShell Cmdlet。
你可以通过运行 `Get-Command` 来检查命令类型。

#### VisibleProviders 
你将需要公开命令需要的任意提供程序。
最常见的是 FileSystem 提供程序，但你可能还需要公开其他提供程序，如 Registry 提供程序。
有关提供程序的简介，请参阅这篇 [Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)（你好，脚本专家）博客文章。
请谨慎公开提供程序 -- 通常，最好定义适用于基础提供程序的函数，而不是在 JEA 会话中直接公开提供程序。
这样一来，你仍可允许用户使用文件、注册表项等，但保留了对其可使用自定义验证逻辑处理**哪些*文件和注册表项的控制权。

<!--HONumber=Jun16_HO1-->


