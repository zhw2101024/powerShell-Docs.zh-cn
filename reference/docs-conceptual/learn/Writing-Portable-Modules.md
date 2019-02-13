---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 编写可移植模块
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677425"
---
# <a name="portable-modules"></a>可移植的模块

Windows PowerShell 面向[.NET Framework][]而为编写的 PowerShell Core [.NET Core][]。 可移植的模块是在 Windows PowerShell 和 PowerShell Core 中的模块。 虽然.NET Framework 和.NET Core 是高度兼容，有可用的 Api 在两者之间的差异。 还有 Api 中的差异在 Windows PowerShell 和 PowerShell Core 中可用。 需要注意这些差异的模块应在这两个环境中使用。

## <a name="porting-an-existing-module"></a>移植现有模块

### <a name="porting-a-pssnapin"></a>移植 PSSnapIn

在 PowerShell Core 中不支持 PowerShell 管理单元 (PSSnapIn)。 但是，很容易将 PSSnapIn 转换为 PowerShell 模块。 通常情况下，PSSnapIn 注册代码处于单个源文件的类派生自[PSSnapIn][]。 从生成; 中删除此源文件不再需要它。

使用[New-modulemanifest][]若要创建新的模块清单，即无需 PSSnapIn 注册代码。 一些 PSSnapIn （如说明） 中的值可以在模块清单中重复使用。

`RootModule`模块清单中的属性应设置为实现 cmdlet 的程序集 (dll) 的名称。

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET 可移植性分析器 (又称 APIPort)

为端口模块为 Windows PowerShell，若要使用 PowerShell Core，开始编写[.NET 可移植性分析器][]。 对已编译程序集以确定是否与.NET Framework、.NET Core 和其他.NET 运行时兼容的模块中使用的.NET Api 运行此工具。 如果它们存在，则该工具建议备用 Api。 否则，可能需要添加[运行时检查][]并限制在特定的运行时中不可用的功能。

## <a name="creating-a-new-module"></a>创建一个新的模块

如果创建一个新的模块，建议是使用[.NET CLI][]。

### <a name="installing-the-powershell-standard-module-template"></a>安装 PowerShell 标准模块模板

一旦安装了.NET CLI，安装的模板库生成一个简单的 PowerShell 模块。
该模块将与 Windows PowerShell、 PowerShell Core、 Windows、 Linux 和 macOS 兼容。

下面的示例演示如何安装模板：

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>创建新的模块项目

安装模板后，可以创建使用该模板的新 PowerShell 模块项目。 在此示例中，示例模块是名为 myModule。

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>生成模块

使用标准.NET CLI 命令来生成项目。

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>测试模块

在生成该模块之后, 可以将其导入并执行示例 cmdlet。

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

以下各节详细说明某些使用此模板的技术。

## <a name="net-standard-library"></a>.NET 标准库

[.NET standard][]是所有.NET 实现中可用的.NET Api 的正式规范。 管理面向.NET Standard 适用于与该版本的.NET Standard 兼容的.NET Framework 和.NET Core 版本的代码。

> [!NOTE]
> 虽然 API 可能存在于.NET Standard，.NET Core 中的 API 实现可能会引发`PlatformNotSupportedException`在运行时，因此若要验证与 Windows PowerShell 和 PowerShell Core，兼容性的最佳做法是为你的模块在这两个环境中运行测试。
> 如果你的模块是要将跨平台还在 Linux 和 macOS 上运行测试。

面向.NET Standard 可帮助确保，随着该模块后，不兼容的 Api 不会意外地获取引入到模块。 在编译时，而不是运行时发现不兼容问题。

但是，它不需要以面向.NET Standard 的模块使用 Windows PowerShell 和 PowerShell Core，只要使用兼容的 Api。 中间语言 (IL) 是两个运行时之间兼容。 你可以面向.NET Framework 4.6.1，这是与.NET Standard 2.0 兼容。 如果不使用.NET Standard 2.0 之外的 Api，然后在模块的工作原理与 PowerShell Core 6 无需重新编译。

## <a name="powershell-standard-library"></a>PowerShell 标准库

[PowerShell 标准][]库是所有的 PowerShell 版本大于或等于该标准的版本中提供的 PowerShell Api 的正式规范。

例如， [PowerShell Standard 5.1][]兼容 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更高版本。

我们建议你使用 PowerShell 标准库模块编译。 该库可确保 Api 的可用性和在 Windows PowerShell 和 PowerShell Core 6 中实现。
PowerShell 标准旨在始终是向前兼容。 使用 PowerShell 标准库 5.1 构建的模块将始终与将来版本的 PowerShell 兼容。

## <a name="module-manifest"></a>模块清单

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>指示使用 Windows PowerShell 和 PowerShell Core 的兼容性

在验证之后，您的模块中适用于 Windows PowerShell 和 PowerShell Core，模块清单应显式指示兼容性通过使用[CompatiblePSEditions][]属性。 值为`Desktop`意味着该模块是使用 Windows PowerShell，而值兼容`Core`意味着该模块与 PowerShell Core 兼容。 包括`Desktop`和`Core`意味着该模块是使用 Windows PowerShell 和 PowerShell Core 兼容。

> [!NOTE]
> `Core` 并不意味着该模块适用于 Windows、 Linux 和 macOS。
> **CompatiblePSEditions** PowerShell v5 中引入了属性。 模块清单，使用**CompatiblePSEditions**属性无法加载 PowerShell v5 之前的版本中。

### <a name="indicating-os-compatibility"></a>指示操作系统兼容性

首先，请验证您的模块中适用于 Linux 和 macOS。 接下来，指示与在模块清单中的这些操作系统的兼容性。 这使用户更轻松地找到你的模块时发布到其操作系统[PowerShell 库][]。

在模块清单中，`PrivateData`属性具有`PSData`子属性。 可选`Tags`属性的`PSData`采用 PowerShell 库中显示的值的数组。 PowerShell 库支持以下兼容性值：

| 标记               | 说明                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | 与 PowerShell Core 6 兼容          |
| PSEdition_Desktop | 使用 Windows PowerShell 的兼容         |
| Windows           | 与 Windows 兼容                    |
| Linux             | 与 Linux （没有特定发行版） 兼容 |
| macOS             | 与 macOS 兼容                      |

例如：

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[运行时检查]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell 标准]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 库]: https://www.powershellgallery.com
[.NET 可移植性分析器]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
