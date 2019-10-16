---
title: 如何编写 PowerShell 模块清单 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367096"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何编写 PowerShell 模块清单

编写 Windows PowerShell 模块后，可以选择性地添加模块清单。 模块清单是一个 PowerShell 脚本文件，可用于包含有关模块的信息。 例如，您可以描述作者，在模块中指定文件（如嵌套模块），运行脚本自定义用户的环境、加载类型和格式化文件、定义系统要求，以及限制模块导出的成员。

## <a name="creating-a-module-manifest"></a>创建模块清单

*模块清单*是一个 Windows PowerShell 数据文件（psd1），用于描述模块的内容并确定如何处理模块。 清单文件本身是一个文本文件，其中包含键和值的哈希表。 您可以通过将清单文件命名为与模块相同的方式将其命名为模块，然后将其放在模块目录的根目录中。

对于仅包含一个 hbase-runner.psm1 或二进制程序集的简单模块，模块清单是可选的。 不过，建议您尽可能使用模块清单，因为它们有助于您组织代码和维护版本信息。 此外，需要使用模块清单来导出安装在全局程序集缓存中的程序集。 支持可更新帮助功能的模块还需要模块清单。 也就是说，可更新帮助使用模块清单中的**HelpInfoUri**键来查找帮助信息（HelpInfo XML）文件，该文件包含模块的已更新帮助文件的位置。 有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>创建和使用模块清单

1. 若要创建模块清单，可以使用以下几个选项：

   1. 直接使用所需的最少信息创建哈希表，并将其保存到与模块同名的 psd1 文件中。 完成此操作后，可以打开该文件，并手动添加相应的值。

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 或者，通过将一个或多个默认值作为参数传入来调用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet。 （请注意，只需要文件的名称便可生成清单。）这将创建一个模块清单，其中包含显式声明的所有清单值，其余部分包含相应的默认值。

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 最后，还可以创建一个空的 psd1 文件，并将本主题底部的模板复制到该文件中，并填写相关值。 在这种情况下，唯一的真正要求是确保文件与模块的名称相同。

2. 将任何其他元素添加到要包含在文件中的清单。

   一般而言，此操作可能会在你喜欢的任何文本编辑器（例如记事本）中完成。 不过，从技术上讲，这是一个包含代码的脚本文件，因此你可能希望在实际的脚本或开发环境（例如 Visual Studio Code）中对其进行编辑。 同样，请注意，清单文件的所有元素都是可选的，但 ModuleVersion 编号除外。

   有关可以在模块清单中使用的密钥和值的说明，请参阅下面的**模块清单元素**。 有关其他信息，请参阅[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 中的参数说明。

3. 或者，您可以选择将其他代码添加到您的模块清单，以解决任何不会被基本模块清单元素覆盖的情况。

   出于安全方面的考虑，PowerShell 将只在模块清单文件中运行一小部分的可用操作。 通常，可以使用**if**语句、算术运算符和比较运算符以及基本 PowerShell 数据类型。

4. 创建模块清单后，可以通过调用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)来对其进行测试（以确认清单中描述的任何路径正确）。

   `Test-ModuleManifest myModuleName.psd1`

5. 请确保模块清单位于包含模块的目录的顶层。

   将模块复制到系统并将其导入时，PowerShell 将使用模块清单导入模块。

6. 或者，您可以通过以点为模型的方式[调用 import-module，](/powershell/module/Microsoft.PowerShell.Core/Import-Module)直接测试模块清单。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模块清单元素

下表描述了可在模块清单中包含的元素

|元素|默认值|描述|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 类型： string|' '|与此清单关联的脚本模块或二进制模块文件。 以前版本的 PowerShell 调用此元素为 ModuleToProcess。<br /><br /> 根模块的可能类型可以为空（这将使其成为**清单**模块）、脚本模块的名称（使其成为**脚本**模块的 hbase-runner.psm1），或二进制模块的名称（.exe 或 .dll，这使其成为**二进制**模块）。 在此元素中放置模块清单的名称（. psd1）或脚本文件（ps1）将导致发生错误。|
|ModuleVersion<br /><br /> 类型： string|1.0|此模块的版本号。 该字符串必须能够转换为 [System.object]。 即 "#. #. #. #. #"。 `Import-Module` 会将它在 **$psModulePath**上找到的第一个模块加载到与该名称匹配的，并且至少有一个 ModuleVersion 作为 `-MinimumVersion` 参数。 若要导入特定版本，请改用 @ no__t-0 参数。<br /><br /> 示例： `ModuleVersion = '1.0'`|
|GUID<br /><br /> 类型： string|自动生成 GUID|用于唯一标识此模块的 ID。 请注意，当前无法按 GUID 导入模块。<br /><br /> 示例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|作者<br /><br /> 类型： string|无|此模块的作者。<br /><br /> 示例： `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 类型： string|Unknown|此模块的公司或供应商。<br /><br /> 示例： `CompanyName = 'Fabrikam'`|
|版权<br /><br /> 类型： string|（c） [currentYear] [Author]。 保留所有权利。|此模块的版权声明。<br /><br /> 示例： `Copyright = '2016 AuthorName. All rights reserved.'`|
|描述<br /><br /> 类型： string|' '|此模块提供的功能的说明。<br /><br /> 示例： `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 类型： string|' '|此模块所需的 Windows PowerShell 引擎的最低版本。 当前有效值为1.0、2.0、3.0、4.0 和5.0。<br /><br /> 示例： `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 类型： string|' '|指定模块所需的 Windows PowerShell 主机的名称。 此名称由 Windows PowerShell 提供。 若要查找主机程序的名称，请在程序中键入： `$host.name`。<br /><br /> 示例： `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 类型： string|' '|此模块所需的最小 Windows PowerShell 主机版本。<br /><br /> 示例： `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 类型： string|' '|此模块所需的 Microsoft .NET Framework 的最低版本。<br /><br /> 示例： `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 类型： string|' '|此模块所需的公共语言运行时（CLR）的最低版本。<br /><br /> 示例： `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 类型： string|' '|此模块需要的处理器体系结构（无、X86、Amd64）。 有效值为 x86、AMD64、IA64 和 None（未知或未指定）。<br /><br /> 示例： `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 类型： [string []]|@()|在导入此模块之前，必须导入到全局环境中的模块。 这会加载列出的任何模块，除非已加载这些模块。 （例如，一些模块可能已由其他模块加载。） 还可以使用 `RequiredVersion` 而不是 `ModuleVersion` 来指定要加载的特定版本。 使用 `ModuleVersion` 时，它将加载最新版本，最少指定版本。<br /><br /> 示例： `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 示例： `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 类型： [string []]|@()|必须在导入此模块之前加载的程序集。<br /><br /> 请注意，与 RequiredModules 不同的是，PowerShell 将加载 RequiredAssemblies （如果尚未加载）。|
|ScriptsToProcess<br /><br /> 类型： [string []]|@()|导入模块时，在调用方的会话状态中运行的脚本（ps1）文件。 这可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 您可以使用这些脚本来准备环境，就像使用登录脚本一样。<br /><br /> 在加载清单中列出的任何模块之前，将运行这些脚本。|
|TypesToProcess<br /><br /> 类型： [string []]|@()|导入此模块时要加载的类型文件（. types.ps1xml）。|
|FormatsToProcess<br /><br /> 类型： [string []]|@()|导入此模块时要加载的格式化文件（. types.ps1xml）。|
|NestedModules<br /><br /> 类型： [string []]|@()|要导入的模块，作为 RootModule/ModuleToProcess 中指定的模块的嵌套模块。<br /><br /> 向此元素添加模块名称类似于从脚本或程序集代码中调用 `Import-Module`。 主要区别是在清单文件中，可以更方便地查看正在加载的内容。 此外，如果模块无法在此处加载，则尚未加载您的实际模块。<br /><br /> 除了其他模块以外，你还可以在此处加载脚本（ps1）文件。 这些文件将在根模块的上下文中执行。 （这等同于根模块中的脚本。）|
|FunctionsToExport<br /><br /> 类型： [string []]|@()|指定模块导出的函数（允许但不允许使用通配符）到调用方的会话状态。 默认情况下，不导出任何函数。 您可以使用此键列出模块导出的函数。<br /><br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有函数都将导出到全局会话状态，除非该链中的模块使用 FunctionsToExport 键限制该函数。<br /><br /> 如果清单还导出函数的别名，则此键可以删除其别名在 AliasesToExport 项中列出的函数，但此键无法向列表中添加函数别名。|
|CmdletsToExport<br /><br /> 类型： [string []]|@()|指定模块导出的 cmdlet （允许使用通配符，但不建议使用）。 默认情况下，不导出任何 cmdlet。 你可以使用此密钥列出模块导出的 cmdlet。<br /><br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有 cmdlet 最终将导出到全局会话状态，除非该链中的模块使用 CmdletsToExport 键限制该 cmdlet。<br /><br /> 如果清单还导出 cmdlet 的别名，此密钥可以删除其别名列在 AliasesToExport 密钥中的 cmdlet，但此密钥不能将 cmdlet 别名添加到该列表中。|
|VariablesToExport<br /><br /> 类型： string|'*'|指定模块导出的变量（允许使用通配符）到调用方的会话状态。 默认情况下，将导出所有变量。 您可以使用此密钥来限制由模块导出的变量。<br /><br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有变量都将被导出到全局会话状态，除非该链中的模块使用 VariablesToExport 键限制了该变量。<br /><br /> 如果清单还导出变量的别名，则此键可以删除在 AliasesToExport 项中列出其别名的变量，但此键不能将变量别名添加到该列表中。|
|AliasesToExport<br /><br /> 类型： [string []]|@()|指定模块导出的别名（允许但不允许使用通配符）到调用方的会话状态。 默认情况下，不导出任何别名。 您可以使用此密钥列出模块导出的别名。<br /><br /> 调用方的会话状态可以是全局会话状态，也可以是嵌套模块的其他模块会话状态。 链接嵌套模块时，嵌套模块导出的所有别名最终都将导出到全局会话状态，除非该链中的模块使用 AliasesToExport 键限制该别名。|
|ModuleList<br /><br /> 类型： [string []]|@()|指定与此模块一起打包的所有模块。 可以按名称（以逗号分隔的字符串形式）或使用 ModuleName 和 GUID 密钥的哈希表输入这些模块。 哈希表还可以具有可选的 ModuleVersion 键。 ModuleList 键旨在充当模块清单。 这些模块不会自动处理。|
|FileList<br /><br /> 类型： [string []]|@()|与此模块一起打包的所有文件的列表。 与 ModuleList 一样，FileList 可以帮助你作为清单列表，而不会进行任何处理。|
|PrivateData<br /><br /> 类型： [对象]|@{...}|指定任何需要传递到由 RootModule/ModuleToProcess 键指定的根模块的私有数据。|
|HelpInfoURI<br /><br /> 类型： string|' '|此模块的 HelpInfo URI。|
|DefaultCommandPrefix<br /><br /> 类型： string|' '|从此模块导出的命令的默认前缀。 使用 `Import-Module` 前缀替代默认前缀。|

## <a name="sample-module-manifest"></a>示例模块清单

下面的示例模块清单显示模块清单中的键和默认值。 此示例是使用 Windows PowerShell 3.0 中的 @no__t cmdlet 创建的。 创建多个模块时，可以使用此 cmdlet 创建一个清单模板，然后可以针对不同的模块对该模板进行修改。

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
