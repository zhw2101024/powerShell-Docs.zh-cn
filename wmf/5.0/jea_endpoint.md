# 创建并连接到 JEA 终结点
若要创建 JEA 终结点，需要创建并注册一个专门配置 PowerShell 会话配置文件，可以使用 **New-PSSessionConfigurationFile** cmdlet 生成该文件。

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

这将创建一个如下所示的会话配置文件： 
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

} 
```
在创建 JEA 终结点时，必须设置以下命令的参数（以及文件中的相应密钥）：
1.  将 SessionType 设置为 RestrictedRemoteServer
2.  将 RunAsVirtualAccount 设置为 **$true**
3.  将 TranscriptPath 设置为目录中的一个位置，每次会话后将“即时权限提升”脚本保存到该位置
4.  将 RoleDefinition 设置为一个哈希表，该哈希表定义哪些组有权访问哪些“角色功能”。  此字段定义**谁**可以在此终结点上执行**什么操作**。   “角色功能”是特殊文件，下面进行简要介绍。


RoleDefinition 字段定义哪些组有权访问哪些角色功能。  “角色功能”是一个文件，它定义将向连接用户公开的一组功能。  你可以使用 **New-PSRoleCapabilityFile** 命令创建“角色功能”。

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

这将生成一个模板角色功能，如下所示：
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

} 

```
要想 JEA 会话配置能使用角色功能，则必须在名为“RoleCapabilities”的目录中将其保存为有效的 PowerShell 模块。 如果需要，一个模块可以有多个角色功能文件。

若要开始配置当用户接到 JEA 会话时可以访问哪些 cmdlet、函数、别名和脚本，请在注释模板后将你自己的规则添加到“角色功能”文件。 要深入了解如何配置“角色功能”，请查看完整的[体验指南](http://aka.ms/JEA)。

最后，完成会话和相关“角色功能”的自定义配置后，通过运行 **Register-PSSessionConfiguration** 注册此会话配置并创建终结点。

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## 连接到 JEA 终结点
连接到 JEA 终结点与连接到任何其他 PowerShell 终结点的工作原理相同。  只需将 JEA 终结点命名为与 **New-PSSession**、**Invoke-Command ** 或 **Enter-PSSession** 的“ConfigurationName”参数相同即可。

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
如果已连接到 JEA 会话，运行你有权访问的列在允许列表中的“角色功能”将会受限。
 如果尝试运行任何不允许你的角色运行的命令，将会遇到错误。

<!--HONumber=Jun16_HO4-->


