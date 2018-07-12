---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: 具有兼容的 PowerShell 版本的模块
ms.openlocfilehash: 653cfa82be9d0150da8d8765c96e35be99497262
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892315"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="1850b-103">具有兼容的 PowerShell 版本的模块</span><span class="sxs-lookup"><span data-stu-id="1850b-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="1850b-104">从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。</span><span class="sxs-lookup"><span data-stu-id="1850b-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="1850b-105">**桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="1850b-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="1850b-106">**核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="1850b-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="1850b-107">当前运行的 PowerShell 版本显示在 $PSVersionTable 的 PSEdition 属性中。</span><span class="sxs-lookup"><span data-stu-id="1850b-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable
```

```output
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

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="1850b-108">模块作者可使用 CompatiblePSEditions 模块清单键声明其模块，使其与一个或多个 PowerShell 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="1850b-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="1850b-109">仅 PowerShell 5.1 或更高版本支持该键。</span><span class="sxs-lookup"><span data-stu-id="1850b-109">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="1850b-110">使用 CompatiblePSEditions 键指定模块清单后，该清单无法导入到较低版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1850b-110">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="1850b-111">可通过 PowerShell 版本筛选列表来获取一列可用模块。</span><span class="sxs-lookup"><span data-stu-id="1850b-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```output
Desktop
Core
```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="1850b-112">模块作者可发布面向 PowerShell 的两个版本（Desktop 和 Core）或其中之一的单一模块</span><span class="sxs-lookup"><span data-stu-id="1850b-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="1850b-113">由于模块作者必须使用 $PSEdition 变量在 RootModule 或模块清单中添加所需的逻辑，因此单一模块可同时在 Desktop 和 Core 版本上运行。</span><span class="sxs-lookup"><span data-stu-id="1850b-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="1850b-114">模块可以有两套以 CoreCLR 和 FullCLR 为目标的已编译 DLL。</span><span class="sxs-lookup"><span data-stu-id="1850b-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="1850b-115">以下是两种使用逻辑打包模块来加载合适的 dll 的选项。</span><span class="sxs-lookup"><span data-stu-id="1850b-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="1850b-116">选项 1：打包面向多个版本和多个 PowerShell 版本的模块</span><span class="sxs-lookup"><span data-stu-id="1850b-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="1850b-117">模块文件夹内容</span><span class="sxs-lookup"><span data-stu-id="1850b-117">Module folder contents</span></span>

- <span data-ttu-id="1850b-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="1850b-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="1850b-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="1850b-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="1850b-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="1850b-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="1850b-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="1850b-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="1850b-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="1850b-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="1850b-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="1850b-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="1850b-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="1850b-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="1850b-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="1850b-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="1850b-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="1850b-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="1850b-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="1850b-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="1850b-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="1850b-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="1850b-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="1850b-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="1850b-135">PSScriptAnalyzer.psd1 文件内容</span><span class="sxs-lookup"><span data-stu-id="1850b-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="1850b-136">PSScriptAnalyzer.psm1 文件内容</span><span class="sxs-lookup"><span data-stu-id="1850b-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="1850b-137">以下逻辑基于当前版本加载所需程序集。</span><span class="sxs-lookup"><span data-stu-id="1850b-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="1850b-138">选项 2：使用 PSD1 文件中的 $PSEdition 变量加载适当的 Dll 和嵌套/必需模块</span><span class="sxs-lookup"><span data-stu-id="1850b-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="1850b-139">在 PS 5.1 或更高版本中，模块清单文件中允许使用 $PSEdition 全局变量。</span><span class="sxs-lookup"><span data-stu-id="1850b-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="1850b-140">使用此变量，模块作者可在模块清单文件中指定条件值。</span><span class="sxs-lookup"><span data-stu-id="1850b-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="1850b-141">可在受限语言模式或数据部分引用 $PSEdition 变量。</span><span class="sxs-lookup"><span data-stu-id="1850b-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="1850b-142">通过 CompatiblePSEditions 键或使用 $PSEdition 变量指定模块清单后，该清单无法导入到较低版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1850b-142">Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>

#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="1850b-143">具有 CompatiblePSEditions 键的示例模块清单</span><span class="sxs-lookup"><span data-stu-id="1850b-143">Sample module manifest file with CompatiblePSEditions key</span></span>

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

#### <a name="module-contents"></a><span data-ttu-id="1850b-144">模块内容</span><span class="sxs-lookup"><span data-stu-id="1850b-144">Module contents</span></span>

```powershell
dir -Recurse
```

```output
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

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="1850b-145">PowerShell 库用户可使用 PSEdition_Desktop 和 PSEdition_Core 标记查找某特定 PowerShell 版本支持的模块列表。</span><span class="sxs-lookup"><span data-stu-id="1850b-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="1850b-146">不带 PSEdition_Desktop 和 PSEdition_Core 标记的模块可以在 PowerShell Desktop 版本上运行。</span><span class="sxs-lookup"><span data-stu-id="1850b-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```

## <a name="more-details"></a><span data-ttu-id="1850b-147">详细信息</span><span class="sxs-lookup"><span data-stu-id="1850b-147">More details</span></span>

[<span data-ttu-id="1850b-148">PSEditions 脚本</span><span class="sxs-lookup"><span data-stu-id="1850b-148">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="1850b-149">PowerShell 库的 PSEditions 支持</span><span class="sxs-lookup"><span data-stu-id="1850b-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)

[<span data-ttu-id="1850b-150">更新模块清单</span><span class="sxs-lookup"><span data-stu-id="1850b-150">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)