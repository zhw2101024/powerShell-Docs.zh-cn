---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 获取详细的帮助信息
ms.openlocfilehash: 3f52de8c9963618c154b119d5f4859a92d61fbda
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030398"
---
# <a name="getting-detailed-help-information"></a>获取详细的帮助信息

PowerShell 包含了详细的帮助文章，其中解释了 PowerShell 概念和 PowerShell 语言。 还有针对每个 cmdlet 和提供程序的帮助文章，以及针对许多函数和脚本的帮助文章。

可以在命令提示符下显示这些帮助文章，或在 [PowerShell](/powershell/scripting/overview) 文档中在线查看这些文章的最近更新版本。

## <a name="getting-help-for-cmdlets"></a>获取有关 cmdlet 的帮助

若要获取有关 PowerShell cmdlet 的帮助，请使用 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet。 例如，若要获取 `Get-ChildItem` cmdlet 的帮助，请键入：

```powershell
Get-Help Get-ChildItem
```

或

```powershell
Get-ChildItem -?
```

甚至可以获取有关 Get-Help cmdlet 的帮助。 例如：

```powershell
Get-Help Get-Help
```

若要在会话中获取所有 cmdlet 帮助文章的列表，请键入：

```powershell
Get-Help -Category Cmdlet
```

若要一次显示每篇帮助文章的一页，请使用 `help` 函数或其别名 `man`。
例如，若要显示 `Get-ChildItem` cmdlet 的帮助信息，请键入

```powershell
man Get-ChildItem
```

或

```powershell
help Get-ChildItem
```

若要显示详细信息，请使用 `Get-Help` cmdlet 的 Detailed 参数。 例如，若要获取有关 `Get-ChildItem` cmdlet 的详细信息，请键入：

```powershell
Get-Help Get-ChildItem -Detailed
```

若要显示帮助文章中的所有内容，请使用 `Get-Help` cmdlet 的 Full 参数。 例如，若要显示 `Get-ChildItem` cmdlet 的帮助文章中的所有内容，请键入：

```powershell
Get-Help Get-ChildItem -Full
```

若要获取有关 cmdlet 的参数的详细帮助，请使用 `Get-Help` cmdlet 的 Parameter 参数。 例如，若要获取 `Get-ChildItem` cmdlet 的所有参数的详细帮助，请键入：

```powershell
Get-Help Get-ChildItem -Parameter *
```

若要仅显示帮助文章中的示例，请使用 `Get-Help` 的 Examples 参数。
例如，若要仅显示 `Get-ChildItem` cmdlet 的帮助文章中的示例，请键入：

```powershell
Get-Help Get-ChildItem -Examples
```

有关如何为你编写的 cmdlet 编写帮助文章的信息，请参阅[如何编写 Cmdlet 帮助](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets)主题。

## <a name="getting-conceptual-help"></a>获取概念帮助

`Get-Help` cmdlet 也会显示有关 PowerShell 中的概念文章（包括有关 PowerShell 语言的文章）的信息。 概念帮助文章以“about_”前缀开头，例如 about_line_editing。 （概念文章的名称必须用英文输入，即使在非英语版本的 PowerShell 中也是如此。）

若要显示概念文章的列表，请键入：

```powershell
Get-Help about_*
```

若要显示某一特别的帮助文章，请键入文章名称，例如：

```powershell
Get-Help about_command_syntax
```

`Get-Help` 的参数（例如 Detailed、Parameter 和 Examples）对概念帮助文章的显示没有影响。

## <a name="getting-help-about-providers"></a>获取有关提供程序的帮助

`Get-Help` cmdlet 显示有关 PowerShell 提供程序的信息。 若要获取有关提供程序的帮助，请键入 `Get-Help`，后跟提供程序名称。 例如，若要获取有关 Registr 提供程序的帮助，请键入：

```powershell
Get-Help registry
```

若要获取会话中的所有提供程序帮助文章的列表，请键入

```powershell
Get-Help -Category provider
```

`Get-Help` 的参数（例如 Detailed、Parameter 和 Examples）对提供程序帮助文章的显示没有影响。

## <a name="getting-help-about-scripts-and-functions"></a>获取有关脚本和函数的帮助

PowerShell 中的许多脚本和函数都有帮助文章。 使用 `Get-Help` cmdlet 显示脚本和函数的帮助文章。

若要显示有关某个函数的帮助，请键入 `Get-Help`，后跟函数名称。 例如，若要获取有关 `Disable-PSRemoting` 函数的帮助，请键入：

```powershell
Get-Help Disable-PSRemoting
```

若要显示有关某个脚本的帮助，请键入该脚本文件的路径。 如果该脚本不位于路径环境变量中列出的路径中，则必须使用完全限定的路径。

例如，如果名为“TestScript.ps1”的脚本位于 C:\\PS-Test 目录中，要显示有关该脚本的帮助文章，请键入：

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

用于显示 cmdlet 帮助的参数也适用于脚本和函数帮助。 但是，在运行 `Get-Help *` 时，不会显示函数和脚本的帮助。

有关为函数和脚本编写帮助文章的信息，请参阅以下文章：

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>在线获取帮助

在线查看帮助文章是获得帮助的最佳方式之一。 在线文章更易于更新并提供最新内容。

若要在线获取帮助，请使用 `Get-Help` cmdlet 的 Online 参数。 PowerShell 附带的所有帮助文章（包括提供程序帮助和概念(关于)帮助文章），都可以在 [PowerShell](/powershell/scripting/powershell-scripting) 文档中在线获取。

> [!NOTE]
> 不能将 Online  参数用于概念 (about_\*) 或提供程序帮助文章。
> 在线帮助一个可选功能，并不适用于每一个 cmdlet、函数或脚本。

例如，若要获取有关 `Get-ChildItem` cmdlett 的帮助文章的在线版本，请键入：

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell 在默认浏览器中打开文章。 如果该帮助文章支持在线帮助，也可以查看该帮助文章的 URL。 URL 将显示在帮助文章的“相关链接”部分中。

例如，若要查看 Add-Computer cmdlet 的在线版本的 URL，请键入：

```powershell
Get-Help Add-Computer
```

该文章“相关链接”部分的第一行如下所示。

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

有关如何提供帮助文章的在线支持的信息，请参阅 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

## <a name="see-also"></a>另请参阅

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
