---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
title: "WMF 5.1 中的 Bug 修复"
ms.openlocfilehash: 137095f50f9f926d3488ff9c1ce8270ddbda63eb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="bug-fixes-in-wmf-51" class="xliff"></a>
# WMF 5.1 中的 Bug 修复#

<a id="bug-fixes" class="xliff"></a>
## Bug 修复 ##

WMF 5.1 中修复了以下值得注意的 bug：

<a id="module-auto-discovery-fully-honors-envpsmodulepath" class="xliff"></a>
### 模块自动发现完全遵循 `$env:PSModulePath` ###

WMF 3 中引入了模块自动发现（调用命令时自动加载模块而无需使用显式 Import-Module）。 引入时，PowerShell 会在使用 `$env:PSModulePath` 之前检查 `$PSHome\Modules` 中的命令。

WMF 5.1 将此行为更改为完全遵循 `$env:PSModulePath`。 这允许定义 PowerShell 提供的命令（例如 `Get-ChildItem`）的用户创作模块自动加载并正确重写内置命令。

<a id="file-redirection-no-longer-hard-codes--encoding-unicode" class="xliff"></a>
### 文件重定向不再硬编码 `-Encoding Unicode` ###

在所有以前版本的 PowerShell 中，无法控制文件重定向运算符使用的文件编码（例如 `Get-ChildItem > out.txt`），因为 PowerShell 添加了 `-Encoding Unicode`。

从 WMF 5.1 开始，现在可以通过设置 `$PSDefaultParameterValues` 来更改重定向的文件编码：

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

<a id="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo" class="xliff"></a>
### 修复了 `System.Reflection.TypeInfo` 成员访问中的回归 ###

WMF 5.0 中引入的回归会破坏 `System.Reflection.RuntimeType` 的成员访问（例如 `[int].ImplementedInterfaces`）。
WMF 5.1 中已修复了此 bug。


<a id="fixed-some-issues-with-com-objects" class="xliff"></a>
### 修复了与 COM 对象相关的一些问题 ###

WMF 5.0 引入了一个新 COM 绑定器，用于对 COM 对象调用方法和访问 COM 对象的属性。 这一新绑定器显著提高了性能，但是同样引入了一些 bug，在 WMF 5.1 中已修复了它们。

<a id="argument-conversions-were-not-always-performed-correctly" class="xliff"></a>
#### 参数转换并不总是正确执行 ####

在以下示例中：

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys 方法需要一个字符串，但是 PowerShell 未将字符转换为字符串，而是将转换延迟到 IDispatch::Invoke，后者使用 VariantChangeType 进行转换，在此示例中，这导致发送键“1”、“7”和“3”而不是预期的 Volume.Mute 键。

<a id="enumerable-com-objects-not-always-handled-correctly" class="xliff"></a>
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

在上面的示例中，WMF 5.0 错误地将 Scripting.Dictionary 写入管道，而不是枚举键/值对。

此更改还解决了 [Connect 上的问题 1752224](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

<a id="ordered-was-not-allowed-inside-classes" class="xliff"></a>
### 不允许在类中使用 `[ordered]` ###

WMF 5.0 引入了会对类中使用的类型文本进行验证的类。  
`[ordered]` 类似于类型文本，但不是真正的 .NET 类型。 WMF 5.0 错误地对类中的 `[ordered]` 报告错误：

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


<a id="help-on-about-topics-with-multiple-versions-does-not-work" class="xliff"></a>
### 有关涉及多个版本的主题的帮助不起作用 ###

在 WMF 5.1 之前，如果安装了模块的多个版本，并且它们都共享帮助主题（例如 about_PSReadline），则 `help about_PSReadline` 会返回多个主题，没有明确的方法来查看实际帮助。

WMF 5.1 通过返回有关最新版本主题的帮助来解决此问题。

`Get-Help` 不提供某种方法，这种方法用于指定希望获取相关帮助的版本。 若要解决此问题，请导航到模块目录，然后使用工具（如自己喜爱的编辑器）来直接查看帮助。 

<a id="powershellexe-reading-from-stdin-stopped-working" class="xliff"></a>
### 从 STDIN 中读取的 powershell.exe 停止运行

客户使用本机应用中的 `powershell -command -` 来执行通过 STDIN 传入脚本的 PowerShell。遗憾的是，由于控制台主机中的其他变更，导致此操作中断。

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

<a id="powershellexe-creates-spike-in-cpu-usage-on-startup" class="xliff"></a>
### powershell.exe 在启动时形成 CPU 使用率峰值

PowerShell 使用 WMI 查询来检查是否是通过组策略启动，以免导致延迟登录。
WMI 查询最终将 tzres.mui.dll 注入系统中的每个进程，因为 WMI Win32_Process 类会尝试检索本地时区信息。
这会导致 wmiprvse（WMI 提供程序主机）出现 CPU 大峰值。
解决方法是使用 Win32 API 调用来获取相同信息，而不是使用 WMI。

