---
title: "WMF 5.1（预览版）中的控制台改进"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 221b8095c15a810c032bd93aafe8ec886af233d9

---

# WMF 5.1（预览版）中的控制台改进#

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



<!--HONumber=Jul16_HO3-->


