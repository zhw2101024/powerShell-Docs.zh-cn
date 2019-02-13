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
# <a name="portable-modules"></a><span data-ttu-id="20b77-103">可移植的模块</span><span class="sxs-lookup"><span data-stu-id="20b77-103">Portable Modules</span></span>

<span data-ttu-id="20b77-104">Windows PowerShell 面向[.NET Framework][]而为编写的 PowerShell Core [.NET Core][]。</span><span class="sxs-lookup"><span data-stu-id="20b77-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="20b77-105">可移植的模块是在 Windows PowerShell 和 PowerShell Core 中的模块。</span><span class="sxs-lookup"><span data-stu-id="20b77-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="20b77-106">虽然.NET Framework 和.NET Core 是高度兼容，有可用的 Api 在两者之间的差异。</span><span class="sxs-lookup"><span data-stu-id="20b77-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="20b77-107">还有 Api 中的差异在 Windows PowerShell 和 PowerShell Core 中可用。</span><span class="sxs-lookup"><span data-stu-id="20b77-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="20b77-108">需要注意这些差异的模块应在这两个环境中使用。</span><span class="sxs-lookup"><span data-stu-id="20b77-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="20b77-109">移植现有模块</span><span class="sxs-lookup"><span data-stu-id="20b77-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="20b77-110">移植 PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="20b77-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="20b77-111">在 PowerShell Core 中不支持 PowerShell 管理单元 (PSSnapIn)。</span><span class="sxs-lookup"><span data-stu-id="20b77-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="20b77-112">但是，很容易将 PSSnapIn 转换为 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="20b77-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="20b77-113">通常情况下，PSSnapIn 注册代码处于单个源文件的类派生自[PSSnapIn][]。</span><span class="sxs-lookup"><span data-stu-id="20b77-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="20b77-114">从生成; 中删除此源文件不再需要它。</span><span class="sxs-lookup"><span data-stu-id="20b77-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="20b77-115">使用[New-modulemanifest][]若要创建新的模块清单，即无需 PSSnapIn 注册代码。</span><span class="sxs-lookup"><span data-stu-id="20b77-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="20b77-116">一些 PSSnapIn （如说明） 中的值可以在模块清单中重复使用。</span><span class="sxs-lookup"><span data-stu-id="20b77-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="20b77-117">`RootModule`模块清单中的属性应设置为实现 cmdlet 的程序集 (dll) 的名称。</span><span class="sxs-lookup"><span data-stu-id="20b77-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="20b77-118">.NET 可移植性分析器 (又称 APIPort)</span><span class="sxs-lookup"><span data-stu-id="20b77-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="20b77-119">为端口模块为 Windows PowerShell，若要使用 PowerShell Core，开始编写[.NET 可移植性分析器][]。</span><span class="sxs-lookup"><span data-stu-id="20b77-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="20b77-120">对已编译程序集以确定是否与.NET Framework、.NET Core 和其他.NET 运行时兼容的模块中使用的.NET Api 运行此工具。</span><span class="sxs-lookup"><span data-stu-id="20b77-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="20b77-121">如果它们存在，则该工具建议备用 Api。</span><span class="sxs-lookup"><span data-stu-id="20b77-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="20b77-122">否则，可能需要添加[运行时检查][]并限制在特定的运行时中不可用的功能。</span><span class="sxs-lookup"><span data-stu-id="20b77-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="20b77-123">创建一个新的模块</span><span class="sxs-lookup"><span data-stu-id="20b77-123">Creating a New Module</span></span>

<span data-ttu-id="20b77-124">如果创建一个新的模块，建议是使用[.NET CLI][]。</span><span class="sxs-lookup"><span data-stu-id="20b77-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="20b77-125">安装 PowerShell 标准模块模板</span><span class="sxs-lookup"><span data-stu-id="20b77-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="20b77-126">一旦安装了.NET CLI，安装的模板库生成一个简单的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="20b77-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="20b77-127">该模块将与 Windows PowerShell、 PowerShell Core、 Windows、 Linux 和 macOS 兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="20b77-128">下面的示例演示如何安装模板：</span><span class="sxs-lookup"><span data-stu-id="20b77-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="20b77-129">创建新的模块项目</span><span class="sxs-lookup"><span data-stu-id="20b77-129">Creating a New Module Project</span></span>

<span data-ttu-id="20b77-130">安装模板后，可以创建使用该模板的新 PowerShell 模块项目。</span><span class="sxs-lookup"><span data-stu-id="20b77-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="20b77-131">在此示例中，示例模块是名为 myModule。</span><span class="sxs-lookup"><span data-stu-id="20b77-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="20b77-132">生成模块</span><span class="sxs-lookup"><span data-stu-id="20b77-132">Building the Module</span></span>

<span data-ttu-id="20b77-133">使用标准.NET CLI 命令来生成项目。</span><span class="sxs-lookup"><span data-stu-id="20b77-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="20b77-134">测试模块</span><span class="sxs-lookup"><span data-stu-id="20b77-134">Testing the Module</span></span>

<span data-ttu-id="20b77-135">在生成该模块之后, 可以将其导入并执行示例 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="20b77-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="20b77-136">以下各节详细说明某些使用此模板的技术。</span><span class="sxs-lookup"><span data-stu-id="20b77-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="20b77-137">.NET 标准库</span><span class="sxs-lookup"><span data-stu-id="20b77-137">.NET Standard Library</span></span>

<span data-ttu-id="20b77-138">[.NET standard][]是所有.NET 实现中可用的.NET Api 的正式规范。</span><span class="sxs-lookup"><span data-stu-id="20b77-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="20b77-139">管理面向.NET Standard 适用于与该版本的.NET Standard 兼容的.NET Framework 和.NET Core 版本的代码。</span><span class="sxs-lookup"><span data-stu-id="20b77-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="20b77-140">虽然 API 可能存在于.NET Standard，.NET Core 中的 API 实现可能会引发`PlatformNotSupportedException`在运行时，因此若要验证与 Windows PowerShell 和 PowerShell Core，兼容性的最佳做法是为你的模块在这两个环境中运行测试。</span><span class="sxs-lookup"><span data-stu-id="20b77-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="20b77-141">如果你的模块是要将跨平台还在 Linux 和 macOS 上运行测试。</span><span class="sxs-lookup"><span data-stu-id="20b77-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="20b77-142">面向.NET Standard 可帮助确保，随着该模块后，不兼容的 Api 不会意外地获取引入到模块。</span><span class="sxs-lookup"><span data-stu-id="20b77-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="20b77-143">在编译时，而不是运行时发现不兼容问题。</span><span class="sxs-lookup"><span data-stu-id="20b77-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="20b77-144">但是，它不需要以面向.NET Standard 的模块使用 Windows PowerShell 和 PowerShell Core，只要使用兼容的 Api。</span><span class="sxs-lookup"><span data-stu-id="20b77-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="20b77-145">中间语言 (IL) 是两个运行时之间兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="20b77-146">你可以面向.NET Framework 4.6.1，这是与.NET Standard 2.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="20b77-147">如果不使用.NET Standard 2.0 之外的 Api，然后在模块的工作原理与 PowerShell Core 6 无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="20b77-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="20b77-148">PowerShell 标准库</span><span class="sxs-lookup"><span data-stu-id="20b77-148">PowerShell Standard Library</span></span>

<span data-ttu-id="20b77-149">[PowerShell 标准][]库是所有的 PowerShell 版本大于或等于该标准的版本中提供的 PowerShell Api 的正式规范。</span><span class="sxs-lookup"><span data-stu-id="20b77-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="20b77-150">例如， [PowerShell Standard 5.1][]兼容 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="20b77-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="20b77-151">我们建议你使用 PowerShell 标准库模块编译。</span><span class="sxs-lookup"><span data-stu-id="20b77-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="20b77-152">该库可确保 Api 的可用性和在 Windows PowerShell 和 PowerShell Core 6 中实现。</span><span class="sxs-lookup"><span data-stu-id="20b77-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="20b77-153">PowerShell 标准旨在始终是向前兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="20b77-154">使用 PowerShell 标准库 5.1 构建的模块将始终与将来版本的 PowerShell 兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="20b77-155">模块清单</span><span class="sxs-lookup"><span data-stu-id="20b77-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="20b77-156">指示使用 Windows PowerShell 和 PowerShell Core 的兼容性</span><span class="sxs-lookup"><span data-stu-id="20b77-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="20b77-157">在验证之后，您的模块中适用于 Windows PowerShell 和 PowerShell Core，模块清单应显式指示兼容性通过使用[CompatiblePSEditions][]属性。</span><span class="sxs-lookup"><span data-stu-id="20b77-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="20b77-158">值为`Desktop`意味着该模块是使用 Windows PowerShell，而值兼容`Core`意味着该模块与 PowerShell Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="20b77-159">包括`Desktop`和`Core`意味着该模块是使用 Windows PowerShell 和 PowerShell Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="20b77-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="20b77-160">`Core` 并不意味着该模块适用于 Windows、 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="20b77-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="20b77-161">**CompatiblePSEditions** PowerShell v5 中引入了属性。</span><span class="sxs-lookup"><span data-stu-id="20b77-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="20b77-162">模块清单，使用**CompatiblePSEditions**属性无法加载 PowerShell v5 之前的版本中。</span><span class="sxs-lookup"><span data-stu-id="20b77-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="20b77-163">指示操作系统兼容性</span><span class="sxs-lookup"><span data-stu-id="20b77-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="20b77-164">首先，请验证您的模块中适用于 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="20b77-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="20b77-165">接下来，指示与在模块清单中的这些操作系统的兼容性。</span><span class="sxs-lookup"><span data-stu-id="20b77-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="20b77-166">这使用户更轻松地找到你的模块时发布到其操作系统[PowerShell 库][]。</span><span class="sxs-lookup"><span data-stu-id="20b77-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="20b77-167">在模块清单中，`PrivateData`属性具有`PSData`子属性。</span><span class="sxs-lookup"><span data-stu-id="20b77-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="20b77-168">可选`Tags`属性的`PSData`采用 PowerShell 库中显示的值的数组。</span><span class="sxs-lookup"><span data-stu-id="20b77-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="20b77-169">PowerShell 库支持以下兼容性值：</span><span class="sxs-lookup"><span data-stu-id="20b77-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="20b77-170">标记</span><span class="sxs-lookup"><span data-stu-id="20b77-170">Tag</span></span>               | <span data-ttu-id="20b77-171">说明</span><span class="sxs-lookup"><span data-stu-id="20b77-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="20b77-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="20b77-172">PSEdition_Core</span></span>    | <span data-ttu-id="20b77-173">与 PowerShell Core 6 兼容</span><span class="sxs-lookup"><span data-stu-id="20b77-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="20b77-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="20b77-174">PSEdition_Desktop</span></span> | <span data-ttu-id="20b77-175">使用 Windows PowerShell 的兼容</span><span class="sxs-lookup"><span data-stu-id="20b77-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="20b77-176">Windows</span><span class="sxs-lookup"><span data-stu-id="20b77-176">Windows</span></span>           | <span data-ttu-id="20b77-177">与 Windows 兼容</span><span class="sxs-lookup"><span data-stu-id="20b77-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="20b77-178">Linux</span><span class="sxs-lookup"><span data-stu-id="20b77-178">Linux</span></span>             | <span data-ttu-id="20b77-179">与 Linux （没有特定发行版） 兼容</span><span class="sxs-lookup"><span data-stu-id="20b77-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="20b77-180">macOS</span><span class="sxs-lookup"><span data-stu-id="20b77-180">macOS</span></span>             | <span data-ttu-id="20b77-181">与 macOS 兼容</span><span class="sxs-lookup"><span data-stu-id="20b77-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="20b77-182">例如：</span><span class="sxs-lookup"><span data-stu-id="20b77-182">Example:</span></span>

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
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell 标准]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 库]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET 可移植性分析器]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
