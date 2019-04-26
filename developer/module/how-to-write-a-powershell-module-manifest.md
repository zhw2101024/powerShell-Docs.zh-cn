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
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082288"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何编写 PowerShell 模块清单

编写完您的 Windows PowerShell 模块，你可以选择添加一个模块清单。 模块清单是您可以使用包含有关模块的信息的 PowerShell 脚本文件。 例如，可以描述作者，指定模块 （如嵌套模块） 中的文件运行脚本以自定义用户的环境中，加载类型和格式设置文件、 定义系统要求和限制模块导出的成员。

## <a name="creating-a-module-manifest"></a>创建模块清单

一个*模块清单*是一个 Windows PowerShell 数据文件 (.psd1)，用于描述了模块的内容并确定如何处理模块。 清单文件本身是包含键和值的哈希表的文本文件。 您链接到模块的模块，与相同命名并将其放置在模块目录的根目录中的清单文件。

对于包含单个.psm1 或二进制程序集的简单模块，模块清单是可选的。 但是，建议使用模块清单，只要有可能，因为它们可帮助您组织您的代码和维护版本控制信息。 此外，模块清单需要导出在全局程序集缓存中安装的程序集。 模块清单，还需要为支持可更新帮助功能的模块。 也就是说，可更新帮助使用**HelpInfoUri**密钥模块清单，若要查找包含该模块的更新的帮助文件的位置的帮助信息 (HelpInfo XML) 文件中。 有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>若要创建和使用模块清单

1. 若要创建模块清单，您具有多个选项：

   1. 直接创建具有必需的最少信息的哈希表，并将其保存到具有相同的名称作为你的模块的.psd1 文件。 完成连接后，可以打开该文件并手动添加相应的值。

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 或者，致电[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet，使用一个或多个默认值作为参数传递。 (请注意，只需要生成一个清单，但是文件的名称。)使用提供的所有清单值你明确声明，并与其余部分包含适当的默认值，这将创建一个模块清单。

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 最后，您可以还创建一个空的.psd1 文件，并将在本主题底部的模板复制到文件，并填写相关的值。 唯一的真正要求在这种情况下会以确保该文件已命名与模块相同。

2. 中的任何其他元素添加到你想要在文件中有清单。

   通常情况下，可能这会在您喜欢，如记事本的任何文本编辑器中。 但是，这从技术上讲是包含的代码，因此你可能想要在实际脚本或开发环境，如 PowerShell ISE 中对其进行编辑的脚本文件。 同样，请注意，清单文件中的所有元素都是可选的除了 ModuleVersion 数。

   键和值可以在模块清单中的说明，请参阅**模块清单元素**下面。 有关其他信息，请参阅中的参数描述[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet。

3. （可选） 你可以选择将额外的代码添加到以下任何方案的基本模块清单元素不会覆盖在模块清单。

   出于安全考虑，PowerShell 将运行的模块清单文件中的只有一小部分可用的操作。 通常，您可以使用**如果**语句、 算术运算符和比较运算符和基本的 PowerShell 数据类型。

4. 创建模块清单后，你可以测试它 （若要确认正确的清单是否中所述的任何路径，） 通过调用[Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)。

   `Test-ModuleManifest myModuleName.psd1`

5. 请确保模块清单位于包含你的模块的目录的顶层。

   当将复制到系统上您的模块，并将其导入时，PowerShell 将使用模块清单导入模块。

6. （可选） 可以直接测试通过调用在模块清单[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)由点 （.） 的清单本身。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模块清单元素

下表描述了可以在模块清单中的元素

|元素|默认值|说明|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 类型： 字符串|' '|脚本模块或二进制模块文件与此清单相关联。 以前版本的 PowerShell 称为 ModuleToProcess 此元素。<br /><br /> 可能的根模块的类型可以为空 (这会使这**清单**模块)，脚本模块的名称 (.psm1，这样，您**脚本**模块)，或二进制模块 （.exe 或.dll 的名称这使它成为**二进制**模块)。 在此元素中放置一个模块清单 (.psd1) 或脚本文件 (.ps1) 的名称会导致错误发生。|
|ModuleVersion<br /><br /> 类型： 字符串|1.0|此模块的版本号。 字符串必须能够将转换为 [System.Version]。 也就是说，#。 #。 #。 #。 #。 `Import-Module` 将加载找到的第一个模块 **$psModulePath** ，其中的名称匹配，但至少高 ModuleVersion，作为`-MinimumVersion`参数。 若要导入特定版本，请使用`-RequiredVersion`参数，而是。<br /><br /> 示例： `ModuleVersion = '1.0'`|
|GUID<br /><br /> 类型： 字符串|自动生成 GUID|用于唯一标识此模块的 ID。 请注意，不能当前导入模块的 GUID。<br /><br /> 示例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|作者<br /><br /> 类型： 字符串|无|此模块的作者。<br /><br /> 示例： `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 类型： 字符串|Unknown|公司或供应商联系，此模块。<br /><br /> 示例： `CompanyName = 'Fabrikam'`|
|版权<br /><br /> 类型： 字符串|（c) [currentYear] [作者]。 保留所有权利。|此模块的版权声明。<br /><br /> 示例： `Copyright = '2016 AuthorName. All rights reserved.'`|
|说明<br /><br /> 类型： 字符串|' '|此模块提供的功能的说明。<br /><br /> 示例： `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 类型： 字符串|' '|此模块所需的 Windows PowerShell 引擎的最低版本。 当前有效的值为 1.0、 2.0、 3.0、 4.0 和 5.0。<br /><br /> 示例： `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 类型： 字符串|' '|指定 Windows PowerShell 主机所需的模块的名称。 通过 Windows PowerShell 提供此名称。 若要在程序中查找主机程序的名称，请键入： `$host.name` 。<br /><br /> 示例： `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 类型： 字符串|' '|此模块所需的 Windows PowerShell 主机的最低版本。<br /><br /> 示例： `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 类型： 字符串|' '|此模块所需的 Microsoft.NET Framework 最低版本。<br /><br /> 示例： `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 类型： 字符串|' '|公共语言运行时 (CLR) 所需的此模块的最低版本。<br /><br /> 示例： `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 类型： 字符串|' '|处理器体系结构 （无、 X86 Amd64） 所需的此模块。 有效值为 x86、AMD64、IA64 和 None（未知或未指定）。<br /><br /> 示例： `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 类型: [字符串 []]|@()|必须导入到全局环境之前导入此模块的模块。 这将加载列出，除非它们已加载任何模块。 （例如，某些模块可能已加载的另一个模块。）。 还有可能要指定特定版本进行加载时，使用`RequiredVersion`而非`ModuleVersion`。 当使用`ModuleVersion`它会加载最少的指定的版本可用的最新版本。<br /><br /> 示例： `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 示例： `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 类型: [字符串 []]|@()|必须在导入此模块之前加载的程序集。<br /><br /> 请注意，与不同的 RequiredModules，PowerShell 将加载 RequiredAssemblies 是否尚未加载。|
|ScriptsToProcess<br /><br /> 类型: [字符串 []]|@()|导入模块调用方的会话状态中运行的脚本 (.ps1) 文件。 这可能是全局会话状态的或对于嵌套模块，另一个模块的会话状态。 可以使用这些脚本来准备环境，就像您可能会使用登录脚本。<br /><br /> 在任何清单中列出的模块加载之前运行这些脚本。|
|TypesToProcess<br /><br /> 类型: [对象 []]|@()|键入要导入此模块时加载的文件 (.ps1xml)。|
|FormatsToProcess<br /><br /> 类型: [对象 []]|@()|设置文件 (.ps1xml) 导入此模块时要加载的格式。|
|NestedModules<br /><br /> 类型: [对象 []]|@()|若要作为嵌套模块的 RootModule/ModuleToProcess 中指定的模块导入的模块。<br /><br /> 将模块名称添加到此元素是类似于调用`Import-Module`从脚本或程序集代码中。 主要区别是，它是更轻松地查看什么要加载此处清单文件中。 此外，如果无法在此处加载模块，你将尚未具有加载实际模块。<br /><br /> 除了其他模块，你可能会加载以下脚本 (.ps1) 文件。 这些文件将在根模块的上下文中执行。 （这相当于圆点溯源根模块中的脚本。）|
|FunctionsToExport<br /><br /> 键入：字符串|'*'|指定到调用方的会话状态模块导出 （允许使用的字符的通配符） 的函数。 默认情况下，导出的所有函数。 可以使用此密钥来限制由模块导出的函数。<br /><br /> 调用方的会话状态可以是全局会话状态的或对于嵌套模块，另一个模块的会话状态。 当链接嵌套的模块，通过嵌套模块导出的所有函数都导出到全局会话状态中，除非使用 FunctionsToExport 密钥链中的模块将限制为该函数。<br /><br /> 如果清单还将导出的函数的别名，此密钥 AliasesToExport 键，可以删除其别名列出的函数，但此键不能将函数的别名添加到列表。|
|CmdletsToExport<br /><br /> 键入：字符串|'*'|指定模块导出 （允许使用的字符的通配符） 的 cmdlet。 默认情况下，导出所有 cmdlet。 可以使用此密钥来限制由模块导出的 cmdlet。<br /><br /> 调用方的会话状态可以是全局会话状态的或对于嵌套模块，另一个模块的会话状态。 当您要串联嵌套的模块时，通过嵌套模块导出的所有 cmdlet 将最终都导出到全局会话状态除非通过使用 CmdletsToExport 密钥链中的模块将限制为该 cmdlet。<br /><br /> 如果清单也会导出别名的 cmdlet，此密钥可以 AliasesToExport 键，删除列出其别名的 cmdlet，但此键不能将 cmdlet 别名添加到列表。|
|VariablesToExport<br /><br /> 键入：字符串|'*'|指定到调用方的会话状态模块导出 （允许使用的字符的通配符） 的变量。 默认情况下，导出所有变量。 可以使用此密钥来限制由模块导出的变量。<br /><br /> 调用方的会话状态可以是全局会话状态的或对于嵌套模块，另一个模块的会话状态。 当您要串联嵌套的模块时，嵌套模块导出的所有变量都导出到全局会话状态中，除非使用 VariablesToExport 密钥链中的模块将限制为该变量。<br /><br /> 如果清单也会导出别名的变量，此密钥可以 AliasesToExport 键，删除列出其别名的变量，但此键不能将变量的别名添加到列表。|
|AliasesToExport<br /><br /> 键入：字符串|'*'|到调用方的会话状态指定模块导出 （允许使用的字符的通配符） 的别名。 默认情况下，导出所有别名。 可以使用此密钥来限制由模块导出的别名。<br /><br /> 调用方的会话状态可以是全局会话状态的或对于嵌套模块，另一个模块的会话状态。 当您要串联嵌套的模块时，嵌套模块导出的所有别名将最终都导出到全局会话状态除非通过使用 AliasesToExport 密钥链中的模块将限制为该别名。|
|ModuleList<br /><br /> 类型: [字符串 []]|@()|指定与此模块，它们打包在所有模块。 可以使用模块名称和 GUID 的密钥中输入名称 （以逗号分隔字符串） 或哈希表作为这些模块。 哈希表也可能具有一个可选的 ModuleVersion 密钥。 ModuleList 键专门用于充当模块清单。 这些模块不会自动处理。|
|文件列表<br /><br /> 类型: [字符串 []]|@()|与此模块打包在一起的所有文件的列表。 使用 ModuleList，文件列表是作为一个清单的列表，帮助您，否则不处理。|
|PrivateData<br /><br /> 类型: [对象]|' '|指定要传递给 RootModule/ModuleToProcess 项指定的根模块所需任何专用数据。|
|HelpInfoURI<br /><br /> 类型： 字符串|' '|此模块的 HelpInfo URI。|
|DefaultCommandPrefix<br /><br /> 类型： 字符串|' '|此模块从导出的命令的默认前缀。 重写默认前缀使用`Import-Module`的前缀。|

## <a name="sample-module-manifest"></a>示例模块清单

下面的示例模块清单模块清单中显示的项和默认值。 此示例中已通过使用`New-ModuleManifest`在 Windows PowerShell 3.0 中的 cmdlet。 在创建多个模块时，可以使用此 cmdlet 来创建稍后可修改为不同的模块清单模板。

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
