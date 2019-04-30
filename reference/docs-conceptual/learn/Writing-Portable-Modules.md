---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 编写可移植模块
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086402"
---
# <a name="portable-modules"></a>可移植模块

Windows PowerShell 是为 [.NET Framework][] 编写的，而 PowerShell Core 是为 [.NET Core][] 编写的。 可移植模块是同时适用于 Windows PowerShell 和 PowerShell Core 的模块。 虽然 .Net Framework 和 .Net Core 高度兼容，但它们之间的可用 API 有所不同。 Windows PowerShell 和 PowerShell Core 中的可用 API 也有所不同。 打算在这两种环境中使用的模块需要了解这些差异。

## <a name="porting-an-existing-module"></a>移植现有模块

### <a name="porting-a-pssnapin"></a>移植 PSSnapIn

PowerShell Core 不支持 PowerShell SnapIn (PSSnapIn)。 然而，将 PSSnapIn 转换为 PowerShell 模块非常简单。 通常，PSSnapIn 注册代码位于派生自 [PSSnapIn][] 的类的单个源文件中。 从生成中删除此源文件；不再需要该文件。

使用 [New-ModuleManifest][] 创建一个新的模块清单，进而无需 PSSnapIn 注册代码。 PSSnapIn 中的一些值（比如 Description）可以在模块清单中重用。

模块清单中的 `RootModule` 属性应设置为实现 cmdlet 的程序集 (dll) 的名称。

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET 可移植性分析器 （又称 APIPort）

若要移植为 Windows PowerShell 编写的模块以使用 PowerShell Core，可以从 [.NET 可移植性分析器][]开始。 对编译后的程序集运行此工具，以确定模块中使用的 .NET API 是否与 .NET Framework、.NET Core 以及其他 .NET 运行时兼容。 工具将建议使用替代 API（若存在）。 否则，可能需要添加[运行时检查][]并限制特定运行时中不可用的功能。

## <a name="creating-a-new-module"></a>创建新模块

如果创建一个新模块，建议使用 [.NET CLI][]。

### <a name="installing-the-powershell-standard-module-template"></a>安装 PowerShell Standard 模块模板

安装 .NET CLI 后，请安装模板库以生成一个简单的 PowerShell 模块。
该模块将与 Windows PowerShell、PowerShell Core、Windows、Linux 和 macOS 兼容。

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

### <a name="creating-a-new-module-project"></a>创建新模块项目

安装模板后，可以使用该模板创建一个新的 PowerShell 模块项目。 在此示例中，示例模块名为“myModule”。

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

使用标准 .NET CLI 命令来生成项目。

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

在生成模块之后，可以导入它并执行示例 cmdlet。

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

以下各节详细说明了此模板使用的一些技术。

## <a name="net-standard-library"></a>.NET Standard 库

[.NET Standard][] 是可在所有 .NET 实现中使用的 .NET API 的正式规范。 以 .NET Standard 为目标的托管代码适用于与该版本的 .NET Standard 兼容的 .NET Framework 和 .NET Core 版本。

> [!NOTE]
> 尽管 .Net Standard 中可能存在 API，但 .Net Core 中的 API 实现可能会在运行时引发 `PlatformNotSupportedException`，因此，要验证与 Windows PowerShell 和 PowerShell Core 的兼容性，最佳做法是在这两个环境中运行模块测试。
> 如果模块是跨平台的，还可以在 Linux 和 macOS 上运行测试。

以 .Net Standard 为目标有助于确保随着模块的发展，不会意外地将不兼容的 API 引入到模块中。 不兼容性是在编译时而不是运行时发现的。

但是，只要使用兼容 API，则不需要以 .NET Standard 为目标来让模块来同时适用于 Windows PowerShell 和 PowerShell Core。 中间语言 (IL) 在两个运行时之间是兼容的。 可面向 .Net Framework 4.6.1，它与 .Net Standard 2.0 兼容。 如果不使用 .Net Standard 2.0 之外的 API，模块将适用于 PowerShell Core 6，而无需重新编译。

## <a name="powershell-standard-library"></a>PowerShell Standard 库

[PowerShell Standard][] 库是 PowerShell API 的正式规范，适用于所有大于或等于该标准版本的 PowerShell 版本。

例如，[PowerShell Standard 5.1][] 与 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本兼容。

建议使用 PowerShell Standard 库编译模块。 该库确保 API 同时适用于 Windows PowerShell 和 PowerShell Core 6 并可在两者中实现。
PowerShell Standard 旨在始终向前兼容。 使用 PowerShell Standard 库 5.1 生成的模块将始终与 PowerShell 的未来版本兼容。

## <a name="module-manifest"></a>模块清单

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>指示与 Windows PowerShell 和 PowerShell Core 的兼容性

在验证模块同时适用于 Windows PowerShell 和 PowerShell Core 之后，模块清单应使用 [CompatiblePSEditions][] 属性显式指示兼容性。 值 `Desktop` 表示模块与 Windows PowerShell 兼容，而值 `Core` 表示模块与 PowerShell Core 兼容。 同时包含 `Desktop` 和 `Core` 意味着该模块同时与 Windows PowerShell 和 PowerShell Core 兼容。

> [!NOTE]
> `Core` 并不自动意味着模块与 Windows、Linux 和 macOS 兼容。
> PowerShell v5 中引入了 CompatiblePSEditions 属性。 在 PowerShell v5 之前的版本中，将无法加载使用 CompatiblePSEditions 属性的模块清单。

### <a name="indicating-os-compatibility"></a>指示操作系统兼容性

首先，验证模块是否适用于 Linux和 macOS。 接下来，在模块清单中指示与这些操作系统的兼容性。 这使得用户在发布到 [PowerShell 库][]时可以更轻松地找到适用于其操作系统的模块。

在模块清单中，`PrivateData` 属性有一个 `PSData` 子属性。 `PSData` 的可选 `Tags` 属性采用一组在 PowerShell 库中显示的值。 PowerShell 库支持以下兼容性值：

| 标记               | 说明                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | 与 PowerShell Core 6 兼容          |
| PSEdition_Desktop | 与 Windows PowerShell 兼容         |
| Windows           | 与 Windows 兼容                    |
| Linux             | 与 Linux（无特定发行版）兼容 |
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
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 库]: https://www.powershellgallery.com
[.NET 可移植性分析器]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
