---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: modulewithpseditionsupport
ms.openlocfilehash: 8122756b78e18fe55daef5c46dc299b87ddcaf1a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="modules-with-compatible-powershell-editions" class="xliff"></a>
# 具有兼容的 PowerShell 版本的模块
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

<a id="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable" class="xliff"></a>
## 正在运行的 PowerShell 版本显示在 $PSVersionTable.的 PSEdition 属性中。
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<a id="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later" class="xliff"></a>
## 模块作者可使用 CompatiblePSEditions 模块清单键声明其模块，使其与一个或多个 PowerShell 版本兼容。 仅 PowerShell 5.1 或更高版本支持该键。
注意 使用 CompatiblePSEditions 键指定模块清单后，该清单无法导入到较低版本的 PowerShell。

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
Desktop
Core

$ModuleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```
可通过 PowerShell 版本筛选列表来获取一列可用模块。
```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

<a id="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core" class="xliff"></a>
## 模块作者可发布面向 PowerShell 的两个版本（Desktop 和 Core）或其中之一的单一模块 

由于模块作者必须使用 $PSEdition 变量在 RootModule 或模块清单中添加所需的逻辑，因此单一模块可同时在 Desktop 和 Core 版本上运行。
模块可以有两套以 CoreCLR 和 FullCLR 为目标的已编译 DLL。
以下是两种使用逻辑打包模块来加载合适的 dll 的选项。

<a id="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell" class="xliff"></a>
### 选项 1：打包面向多个版本和多个 PowerShell 版本的模块

<a id="module-folder-contents" class="xliff"></a>
#### 模块文件夹内容
- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

<a id="contents-of-psscriptanalyzerpsd1-file" class="xliff"></a>
#### PSScriptAnalyzer.psd1 文件内容

```powershell
@{
 
# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<a id="contents-of-psscriptanalyzerpsm1-file" class="xliff"></a>
#### PSScriptAnalyzer.psm1 文件内容
以下逻辑基于当前版本加载所需程序集。

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }    
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
} 

```

<a id="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules" class="xliff"></a>
### 选项 2：使用 PSD1 文件中的 $PSEdition 变量加载适当的 Dll 和嵌套/必需模块

在 PS 5.1 或更高版本中，模块清单文件中允许使用 $PSEdition 全局变量。
使用此变量，模块作者可在模块清单文件中指定条件值。 可在受限语言模式或数据部分引用 $PSEdition 变量。 

注意 通过 CompatiblePSEditions 键或使用 $PSEdition 变量指定模块清单后，该清单无法导入到较低版本的 PowerShell。


<a id="sample-module-manifest-file-with-compatiblepseditions-key" class="xliff"></a>
#### 具有 CompatiblePSEditions 键的示例模块清单

```powershell
@{ 
# - - -
 
# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}
 
# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'
 
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}
 
# -- - -
}
```

<a id="module-contents" class="xliff"></a>
#### 模块内容

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
d-----         7/5/2016   1:37 PM                clr                                                                                 
d-----         7/5/2016   1:36 PM                coreclr                                                                             
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1                                                             
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl                                                                      
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl                                                                      
```

<a id="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditoncore" class="xliff"></a>
## PowerShell 库用户可使用 PSEdition_Desktop 和 PSEditon_Core 标记查找某特定 PowerShell 版本支持的模块列表。
不带 PSEdition_Desktop 和 PSEditon_Core 标记的模块可以在 PowerShell Desktop 版本上运行。

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEditon_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEditon_Core

```


<a id="more-details" class="xliff"></a>
## 详细信息
<a id="scripts-with-pseditionsscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [PSEditions 脚本](../script/scriptwithpseditionsupport.md)
<a id="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd" class="xliff"></a>
### [PowerShell 库的 PSEditions 支持](../../psgallery/psgallery_pseditions.md)
<a id="update-module-manifest-psgetupdate-modulemanifestmd" class="xliff"></a>
### [更新模块清单] (./psget_update-modulemanifest.md)

