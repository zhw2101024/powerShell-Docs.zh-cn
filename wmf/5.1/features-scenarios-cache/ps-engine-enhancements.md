---
title: "PowerShell 引擎增强功能"
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 6813902aec214aee9ede27ff79dd291364e9f443
ms.openlocfilehash: f864850128f118704d7545b09110835ab1d51b8e

---

# PowerShell 引擎增强功能 #

对于 PowerShell 5.1，实现了针对核心 PowerShell 引擎的以下改进：


## 性能 ##

性能在一些重要方面得到了改进：

1. 启动
2. 向 ForEach-Object 和 Where-Object 这类 cmdlet 进行管道传递的速度大约提供了 50% 

一些示例改进（结果可能因硬件而异）： 

| 方案 | 5.0 时间（毫秒） | 5.1 时间（毫秒） |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次运行： `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 构建的命令分析缓存： `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
与启动相关的一个更改可能会影响某些（不支持的）方案。 PowerShell 不再读取文件 `$pshome\*.ps1xml` - 这些文件已转换为 C#，以避免处理 xml 文件的某些文件和 cpu 开销。 这些文件仍存在，以同时支持 V2，因此如果更改文件内容，则不会对 V5 产生任何影响，只会影响 V2。 请注意，更改这些文件的内容从来都不是受支持的方案。

另一个显著更改是 PowerShell 如何为系统上安装的模块缓存导出的命令和其他信息。 以前，此缓存存储在目录 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 中。 在 WMF 5.1 中，此缓存是单个文件 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`。
有关详细信息，请参阅 [analysis_cache.md]()。

从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。



## Bug 修复 ##

修复了以下值得注意的 bug：

### 模块自动发现完全遵循 `$env:PSModulePath` ###

WMF3 中引入了模块自动发现（调用命令时自动加载模块而无需使用显式 Import-Module）。 引入时，PowerShell 会在使用 `$env:PSModulePath` 之前检查 `$PSHome\Modules` 中的命令。

WMF5.1 将此行为更改为完全遵循 `$env:PSModulePath`。 这允许定义 PowerShell 提供的命令（例如 `Get-ChildItem`）的用户创作模块自动加载并正确重写内置命令。

### 文件重定向不再硬编码 `-Encoding Unicode` ###

在所有以前版本的 PowerShell 中，无法控制文件重定向运算符使用的文件编码（例如 `get-childitem > out.txt`），因为 PowerShell 添加了 `-Encoding Unicode`。

从 WMF 5.1 开始，现在可以通过设置 `$PSDefaultParameterValues` 来更改重定向的文件编码，例如

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### 修复了成员访问中的回归 `System.Reflection.TypeInfo` ###

WMF5 中引入的回归会破坏 `System.Reflection.RuntimeType` 的成员访问（例如 `[int].ImplementedInterfaces`）。
WMF5.1 中已修复了此 bug。


### 修复了与 COM 对象相关的一些问题 ###

WMF5 引入了一个新 COM 绑定器，用于对 COM 对象调用方法和访问 COM 对象的属性。
这一新绑定器显著提高了性能，但是同样引入了一些 bug，在 WMF5.1 中已修复了它们。

#### 参数转换并不总是正确执行 ####

在以下示例中：

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

SendKeys 方法需要一个字符串，但是 PowerShell 未将字符转换为字符串，而是将转换延迟到 IDispatch::Invoke，后者使用 VariantChangeType 进行转换，在此示例中，这导致发送键“1”、“7”和“3”而不是预期的 Volume.Mute 键。

#### 可枚举 COM 对象并不总是正确处理 ####

PowerShell 通常可枚举大多数可枚举对象，但是在 WMF5 中引入的回归会阻止实现 IEnumerable 的 COM 对象的枚举。  例如：

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

在上面的示例中，WMF5 错误地将 Scripting.Dictionary 写入管道，而不是枚举键值对。


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

在 WMF5.1 之前，如果安装了模块的多个版本，并且它们都共享帮助主题（例如 about_PSReadline），则 `help about_PSReadline` 会返回多个主题，没有明确的方法来查看实际帮助。

WMF5.1 通过返回有关最新版本主题的帮助来解决此问题。

Get-Help 未提供用于指定你希望获取相关帮助的版本的方法，解决方法是导航到模块目录，然后使用工具（如自己喜爱的编辑器）来直接查看帮助。 



<!--HONumber=Jul16_HO2-->


