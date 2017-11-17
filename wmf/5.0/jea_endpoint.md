---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: c3645a6ba83081bd5ac31a13af0f67f6538db22a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="cc32d-102">创建并连接到 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="cc32d-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="cc32d-103">若要创建 JEA 终结点，需要创建并注册一个专门配置 PowerShell 会话配置文件，可以使用 **New-PSSessionConfigurationFile** cmdlet 生成该文件。</span><span class="sxs-lookup"><span data-stu-id="cc32d-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

<span data-ttu-id="cc32d-104">这将创建一个如下所示的会话配置文件：</span><span class="sxs-lookup"><span data-stu-id="cc32d-104">This will create a session configuration file that looks like this:</span></span> 
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
<span data-ttu-id="cc32d-105">在创建 JEA 终结点时，必须设置以下命令的参数（以及文件中的相应密钥）：</span><span class="sxs-lookup"><span data-stu-id="cc32d-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="cc32d-106">将 SessionType 设置为 RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="cc32d-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="cc32d-107">将 RunAsVirtualAccount 设置为 **$true**</span><span class="sxs-lookup"><span data-stu-id="cc32d-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="cc32d-108">将 TranscriptPath 设置为目录中的一个位置，每次会话后将“即时权限提升”脚本保存到该位置</span><span class="sxs-lookup"><span data-stu-id="cc32d-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="cc32d-109">将 RoleDefinition 设置为一个哈希表，该哈希表定义哪些组有权访问哪些“角色功能”。</span><span class="sxs-lookup"><span data-stu-id="cc32d-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="cc32d-110">此字段定义**谁**可以在此终结点上执行**什么操作**。</span><span class="sxs-lookup"><span data-stu-id="cc32d-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="cc32d-111">“角色功能”是特殊文件，下面进行简要介绍。</span><span class="sxs-lookup"><span data-stu-id="cc32d-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="cc32d-112">RoleDefinition 字段定义哪些组有权访问哪些角色功能。</span><span class="sxs-lookup"><span data-stu-id="cc32d-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="cc32d-113">“角色功能”是一个文件，它定义将向连接用户公开的一组功能。</span><span class="sxs-lookup"><span data-stu-id="cc32d-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="cc32d-114">你可以使用 **New-PSRoleCapabilityFile** 命令创建“角色功能”。</span><span class="sxs-lookup"><span data-stu-id="cc32d-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

<span data-ttu-id="cc32d-115">这将生成一个模板角色功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc32d-115">This will generate a template role capability that looks like this:</span></span>
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
<span data-ttu-id="cc32d-116">要想 JEA 会话配置能使用角色功能，则必须在名为“RoleCapabilities”的目录中将其保存为有效的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="cc32d-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="cc32d-117">如果需要，一个模块可以有多个角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="cc32d-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="cc32d-118">若要开始配置当用户接到 JEA 会话时可以访问哪些 cmdlet、函数、别名和脚本，请在注释模板后将你自己的规则添加到“角色功能”文件。</span><span class="sxs-lookup"><span data-stu-id="cc32d-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="cc32d-119">要深入了解如何配置“角色功能”，请查看完整的[体验指南](http://aka.ms/JEA)。</span><span class="sxs-lookup"><span data-stu-id="cc32d-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="cc32d-120">最后，完成会话和相关“角色功能”的自定义配置后，通过运行 **Register-PSSessionConfiguration** 注册此会话配置并创建终结点。</span><span class="sxs-lookup"><span data-stu-id="cc32d-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="cc32d-121">连接到 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="cc32d-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="cc32d-122">连接到 JEA 终结点与连接到任何其他 PowerShell 终结点的工作原理相同。</span><span class="sxs-lookup"><span data-stu-id="cc32d-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="cc32d-123">只需将 JEA 终结点命名为与 **New-PSSession**、**Invoke-Command**  或 **Enter-PSSession** 的“ConfigurationName”参数相同即可。</span><span class="sxs-lookup"><span data-stu-id="cc32d-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="cc32d-124">如果已连接到 JEA 会话，运行你有权访问的列在允许列表中的“角色功能”将会受限。
</span><span class="sxs-lookup"><span data-stu-id="cc32d-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="cc32d-125">如果尝试运行任何不允许你的角色运行的命令，将会遇到错误。</span><span class="sxs-lookup"><span data-stu-id="cc32d-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>

