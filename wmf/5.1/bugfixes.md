---
title: "WMF 5.1 中的 Bug 修复"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 09316fef0594697a60a1bd4acabf39588f75edc2
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="bug-fixes-in-wmf-51"></a>WMF 5.1 中的 Bug 修复#

## <a name="bug-fixes"></a>Bug 修复 ##

WMF 5.1 中修复了以下值得注意的 bug：

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>模块自动发现完全遵循 `$env:PSModulePath` ###

WMF 3 中引入了模块自动发现（调用命令时自动加载模块而无需使用显式 Import-Module）。 引入时，PowerShell 会在使用 `$env:PSModulePath` 之前检查 `$PSHome\Modules` 中的命令。

WMF 5.1 将此行为更改为完全遵循 `$env:PSModulePath`。 这允许定义 PowerShell 提供的命令（例如 `Get-ChildItem`）的用户创作模块自动加载并正确重写内置命令。

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>文件重定向不再硬编码 `-Encoding Unicode` ###

在所有以前版本的 PowerShell 中，无法控制文件重定向运算符使用的文件编码（例如 `Get-ChildItem > out.txt`），因为 PowerShell 添加了 `-Encoding Unicode`。

从 WMF 5.1 开始，现在可以通过设置 `$PSDefaultParameterValues` 来更改重定向的文件编码：

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>修复了 `System.Reflection.TypeInfo` 成员访问中的回归 ###

WMF 5.0 中引入的回归会破坏 `System.Reflection.RuntimeType` 的成员访问（例如 `[int].ImplementedInterfaces`）。
WMF 5.1 中已修复了此 bug。


### <a name="fixed-some-issues-with-com-objects"></a>修复了与 COM 对象相关的一些问题 ###

WMF 5.0 引入了一个新 COM 绑定器，用于对 COM 对象调用方法和访问 COM 对象的属性。 这一新绑定器显著提高了性能，但是同样引入了一些 bug，在 WMF 5.1 中已修复了它们。

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>参数转换并不总是正确执行 ####

在以下示例中：

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys 方法需要一个字符串，但是 PowerShell 未将字符转换为字符串，而是将转换延迟到 IDispatch::Invoke，后者使用 VariantChangeType 进行转换，在此示例中，这导致发送键“1”、“7”和“3”而不是预期的 Volume.Mute 键。

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>可枚举 COM 对象并不总是正确处理 ####

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

### <a name="ordered-was-not-allowed-inside-classes"></a>不允许在类中使用 `[ordered]` ###

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


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>有关涉及多个版本的主题的帮助不起作用 ###

在 WMF 5.1 之前，如果安装了模块的多个版本，并且它们都共享帮助主题（例如 about_PSReadline），则 `help about_PSReadline` 会返回多个主题，没有明确的方法来查看实际帮助。

WMF 5.1 通过返回有关最新版本主题的帮助来解决此问题。

`Get-Help` 不提供某种方法，这种方法用于指定希望获取相关帮助的版本。 若要解决此问题，请导航到模块目录，然后使用工具（如自己喜爱的编辑器）来直接查看帮助。 
