---
title: "WMF 5.1 中的新方案和功能（预览版）"
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# WMF 5.1 中的新方案和功能（预览版） #

> 注意：此信息是预发布版本，可能会进行更改。

## PowerShell 版本 ##
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

**详细了解如何使用 PowerShell 版本**
- [确定正在运行的 PowerShell 版本]()
- [声明模块与特定 PowerShell 版本的兼容性]()
- [按 CompatiblePSEditions 筛选 Get-Module 结果]()
- [阻止脚本执行，除非在 PowerShell 的兼容版本上运行]()

## 模块分析缓存 ##
从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。

默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。
缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。

若要更改缓存的默认位置，请在启动 PowerShell 之前设置环境变量 PSModuleAnalysisCachePath。 对此环境变量进行的更改只影响子进程。
值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。
若要禁用文件缓存，请将此值设置为无效位置，例如：

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

这会将路径设置为无效设备。 如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过跟踪器进行报告的错误：

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。
有时不需要这些检查，在这种情况下可以通过设置关闭它们

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此环境变量的设置会在当前进程中立即生效。

##指定模块版本

在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。 以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。


在 WMF 5.1 中：

* 可以使用 `ModuleSpecification` [哈希表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。

**例如：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。

## PowerShell 控制台改进

在 WMF 5.1 中对 Powershell.exe 进行了以下更改以改进控制台体验：

###VT100 支持

Windows 10 添加了对 [VT100 转义序列](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx)的支持。
计算表宽度时，PowerShell 会忽略某些 VT100 格式设置转义序列。

PowerShell 还添加了一个新 API，它可以在格式设置代码中用于确定是否支持 VT100。 例如：

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
下面是一个完整[示例](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)，可以用于突出显示来自 Select-String 的匹配项。
将该示例保存在名为 `MatchInfo.format.ps1xml` 的文件中，随后若要在配置文件或其他位置使用它，请运行 `Update-FormatData -Prepend MatchInfo.format.ps1xml`。

请注意，VT100 转义序列仅从 Windows 10 Aniversary 更新开始受支持；它们在早期系统上不受支持。   

### PSReadline 中的 Vi 模式支持

[PSReadline](https://github.com/lzybkr/PSReadLine) 添加了对 vi 模式的支持。 若要使用 vi 模式，请运行 `Set-PSReadline -EditMode vi`。

### 带交互式输入的重定向 stdin 

在早期版本中，重定向 stdin 以及你要以交互方式输入命令时，需要使用 `powershell -File -` 启动 PowerShell。

借助 WMF 5.1，不再需要这一难以发现的选项，你可以在不使用任何选项的情况下启动 powershell，例如 `powershell`。

请注意，PSReadline 当前不支持重定向 stdin，使用重定向 stdin 的内置命令行编辑体验极其有限，例如箭头键不起作用。  PSReadline 的未来版本应该会解决此问题。   

##PowerShell 引擎改进

在 WMF 5.1 中，实现了针对核心 PowerShell 引擎的以下改进：


## 性能 ##

性能在一些重要方面得到了改进：

- 启动
- 向 ForEach-Object 和 Where-Object 这类 cmdlet 进行管道传递的速度大约提供了 50% 

一些示例改进（结果可能因硬件而异）： 

| 方案 | 5.0 时间（毫秒） | 5.1 时间（毫秒） |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次运行： `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 构建的命令分析缓存： `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> 与启动相关的一个更改可能会影响某些不支持的方案。 PowerShell 不再读取文件 `$pshome\*.ps1xml` - 这些文件已转换为 C#，以避免处理 XML 文件的某些文件和 CPU 开销。 这些文件仍存在，以同时支持 V2，因此如果更改文件内容，则不会对 V5 产生任何影响，只会影响 V2。 请注意，更改这些文件的内容从来都不是受支持的方案。

另一个显著更改是 PowerShell 如何为系统上安装的模块缓存导出的命令和其他信息。 以前，此缓存存储在目录 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 中。 在 WMF 5.1 中，此缓存是单个文件 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`。
有关详细信息，请参阅 [analysis_cache.md]()。



## Bug 修复 ##

修复了以下值得注意的 bug：

### 模块自动发现完全遵循 `$env:PSModulePath` ###

WMF 3 中引入了模块自动发现（调用命令时自动加载模块而无需使用显式 Import-Module）。 引入时，PowerShell 会在使用 `$env:PSModulePath` 之前检查 `$PSHome\Modules` 中的命令。

WMF 5.1 将此行为更改为完全遵循 `$env:PSModulePath`。 这允许定义 PowerShell 提供的命令（例如 `Get-ChildItem`）的用户创作模块自动加载并正确重写内置命令。

### 文件重定向不再硬编码 `-Encoding Unicode` ###

在所有以前版本的 PowerShell 中，无法控制文件重定向运算符使用的文件编码（例如 `get-childitem > out.txt`），因为 PowerShell 添加了 `-Encoding Unicode`。

从 WMF 5.1 开始，现在可以通过设置 `$PSDefaultParameterValues` 来更改重定向的文件编码，例如

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### 修复了成员访问中的回归 `System.Reflection.TypeInfo` ###

WMF 5.0 中引入的回归会破坏 `System.Reflection.RuntimeType` 的成员访问（例如 `[int].ImplementedInterfaces`）。
WMF5.1 中已修复了此 bug。


### 修复了与 COM 对象相关的一些问题 ###

WMF 5.0 引入了一个新 COM 绑定器，用于对 COM 对象调用方法和访问 COM 对象的属性。
这一新绑定器显著提高了性能，但是同样引入了一些 bug，在 WMF5.1 中已修复了它们。

#### 参数转换并不总是正确执行 ####

在以下示例中：

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

SendKeys 方法需要一个字符串，但是 PowerShell 未将字符转换为字符串，而是将转换延迟到 IDispatch::Invoke，后者使用 VariantChangeType 进行转换，在此示例中，这导致发送键“1”、“7”和“3”而不是预期的 Volume.Mute 键。

#### 可枚举 COM 对象并不总是正确处理 ####

PowerShell 通常可枚举大多数可枚举对象，但是在 WMF 5.0 中引入的回归会阻止实现 IEnumerable 的 COM 对象的枚举。  例如：

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

在上面的示例中，WMF 5.0 错误地将 Scripting.Dictionary 写入管道，而不是枚举键值对。


### `[ordered]` 不允许在类中使用 ###

WMF5 引入了会对类中使用的类型文本进行验证的类。  `[ordered]` 类似于类型文本，但不是成为真正的 .Net 类型。  WMF5 错误地对类中的 `[ordered]` 报告错误：

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### 有关涉及多个版本的主题的帮助不起作用 ###

在 WMF 5.1 之前，如果安装了模块的多个版本，并且它们都共享帮助主题（例如 about_PSReadline），则 `help about_PSReadline` 会返回多个主题，没有明确的方法来查看实际帮助。

WMF 5.1 通过返回有关最新版本主题的帮助来解决此问题。

Get-Help 未提供用于指定你希望获取相关帮助的版本的方法。 若要解决此问题，请导航到模块目录，然后使用工具（如自己喜爱的编辑器）来直接查看帮助。 

## OneGet 改进
WMF 5.1 包含一些修复和改进，用于解决 WMF 5.0 版本中的一些用户体验缺口。 

###删除了版本别名

**情形**：如果你在系统上安装了包 P1 的版本 1.0 和 2.0，并且要卸载版本 1.0，则会运行“uninstall-package -name P1 -version 1.0”，并且预计在运行该 cmdlet 之后将卸载版本 1.0。 但是结果是卸载了版本 2.0。 
    
出现此问题是因为“-version”参数是“-minimumversion”参数的别名。 当 OneGet 查找具有最低版本 1.0 的合格包时，它会返回最新版本。 在正常情况下需要此行为，因为查找最新版本通常是所需结果。 但是，它不应该应用于 uninstall-package 情况。
    
**解决方案**：在 WMF 5.1 中，在 OneGet 和 PowerShellGet 中完全删除了 -version 别名。 

###多个用于启动 NuGet 提供程序的提示

**情形**：在计算机上首次运行 Find-Module 或 Install-module 或是其他 OneGet cmdlet 时，OneGet 会尝试启动 NuGet 提供程序。 它这样做是因为 PowerShellGet 提供程序还使用 NuGet 提供程序来下载 PowerShell 模块。 OneGet 随后会提示用户输入安装 NuGet 提供程序的权限。 用户选择“yes”进行启动之后，会安装最新版本的 NuGet 提供程序。 
    
但是在某些情况下，当在计算机上安装了旧版本的 NuGet 提供程序时，较旧版本的 NuGet 有时会先加载到 PowerShell 会话中（这是 OneGet 中的争用条件）。 但是 PowerShellGet 需要更新版本的 NuGet 提供程序来正常运行，因此 PowerShellGet 会要求 OneGet 再次启动 NuGet 提供程序。 这会导致出现多个用于启动 NuGet 提供程序的提示。

**解决方案**：在 WMF 5.1 中，OneGet 现在加载最新版本的 NuGet 提供程序，以避免出现多个用于启动 NuGet 提供程序的提示。

还可以通过手动删除旧版本的 NuGet 提供程序（NuGet-Anycpu.exe，如果在 $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies 中存在）来解决此问题


###在仅具有 intranet 访问的计算机上支持 OneGet

**情形**：在 WMF 5.0 中，OneGet 不支持仅具有 intranet（但没有 internet）访问的计算机。

**解决方案**：在 WMF 5.1 中，可以按照以下步骤允许 intranet 计算机使用 OneGet：

1. 使用 Install-PackageProvider NuGet，通过具有 internet 连接的其他计算机下载 NuGet 提供程序。

2. 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下查找 NuGet 提供程序。 

3. 将二进制文件复制到 intranet 计算机可以访问的文件夹或网络共享位置，然后使用“Install-PackageProvider NuGet -Source <Path to folder>”安装 NuGet 提供程序。


###事件日志记录改进

安装包时，你会更改计算机的状态。 在 WMF 5.1 中，OneGet 现在针对安装、卸载和保存包活动将事件记录到 Windows 事件日志中。 事件通道在操作方面与 PowerShell 相同，即，Microsoft-Windows-PowerShell。

###对基本身份验证的支持

在 WMF 5.1 中，OneGet 支持从需要基本身份验证的存储库查找和安装包。 你可以向 Find-Package 和 Install-Package cmdlet 提供凭据。 例如：

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###支持在代理后面使用 OneGet

在 WMF 5.1 中，OneGet 现在采用新的代理参数：-ProxyCredential 和 -Proxy。 使用这些参数可以向 OneGet cmdlet 指定代理 URL 和凭据。 默认情况下，会使用系统代理设置。 例如：

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


