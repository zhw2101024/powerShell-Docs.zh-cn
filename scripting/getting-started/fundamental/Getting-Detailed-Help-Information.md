---
title:  获取详细的帮助信息
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6fb4daf7-8607-4a3e-b692-f77631adc1b9
---

# 获取详细的帮助信息
Windows PowerShell 包含了详细的帮助主题，其中解释了 Windows PowerShell 概念和 Windows PowerShell 语言。 还有针对每个 cmdlet 和提供程序的帮助主题，以及针对许多函数和脚本的帮助主题。

可以在命令提示符下显示这些帮助主题，或在 Microsoft TechNet 库中查看这些主题的最近更新的版本。 许多托管 Windows PowerShell 的程序（如 Windows PowerShell 集成脚本环境）提供了其他帮助功能，如区分上下文的帮助和编译的帮助文件 (.chm)。

## 获取有关 Cmdlet 的帮助
若要获取有关 Windows PowerShell cmdlet 的帮助，请使用 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet。 例如，若要获取 [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet 的帮助，请键入：

```
get-help get-childitem
```

或

```
get-childitem -?
```

甚至可以获取有关 Get-Help cmdlet 的帮助。 例如：

```
get-help get-help
```

若要在会话中获取所有 cmdlet 帮助主题的列表，请键入：

```
get-help -category cmdlet
```

若要一次显示每个帮助主题一页，请使用 **help** 函数或其别名 **man**。 例如，若要显示有关 Get-ChildItem cmdlet 的帮助，请键入：

```
man get-childitem
```

或

```
help get-childitem
```

若要显示有关 cmdlet、函数或脚本的详细信息，包括其参数的说明和其用法的示例，请使用 Get-Help cmdlet 的 *Detailed* 参数。 例如，若要获取有关 Get-ChildItem cmdlet 的详细信息，请键入：

```
get-help get-childitem -detailed
```

若要显示帮助主题中的所有内容，请使用 Get-Help cmdlet 的 *Full* 参数。 例如，若要显示 Get-ChildItem cmdlet 的帮助主题中的所有内容，请键入：

```
get-help get-childitem -full
```

若要获取有关 cmdlet 的参数的详细帮助，请使用 Get-Help cmdlet 的 *Parameter* 参数。 例如，若要获取 Get-ChildItem cmdlet 的所有参数的详细帮助，请键入：

```
get-help get-childitem -parameter *
```

若要仅显示帮助主题中的示例，请使用 Get-Help 的 *Example* 参数。 例如，若要仅显示 Get-ChildItem cmdlet 的帮助主题中的示例，请键入：

```
get-help get-childitem -examples
```

有关如何为你编写的 cmdlet 编写帮助主题的信息，请参阅 MSDN 中的“如何编写 Cmdlet 帮助”主题。

## 获取概念帮助
Get-Help cmdlet 也将显示有关 Windows PowerShell 中的概念主题（包括有关 Windows PowerShell 语言的主题）的信息。 概念主题以“about_”前缀开头，例如 about_line_editing。 （概念主题的名称必须用英文输入，即使在非英语版本的 Windows PowerShell 中也是如此。）

若要显示概念主题的列表，请键入：

```
get-help about_*
```

若要显示某一特别的帮助主题，请键入主题名称，例如：

```
get-help about_command_syntax
```

Get-Help 的参数，例如 *Detailed*、*Parameter* 和 *Examples*，它们对概念帮助主题的显示没有影响。

## 获取有关提供程序的帮助
Get-Help cmdlet 显示有关 Windows PowerShell 提供程序的信息。 若要获取有关提供程序的帮助，请键入“Get-Help”，后跟提供程序名称。 例如，若要获取有关 Registr 提供程序的帮助，请键入：

```
get-help registry
```

若要获取会话中的所有提供程序帮助主题的列表，请键入：

```
get-help -category provider
```

Get-Help 的参数，例如 *Detailed*、*Parameter* 和 *Examples*，它们对提供程序帮助主题的显示没有影响。

## 获取有关脚本和函数的帮助
Windows PowerShell 中的许多脚本和函数都有帮助主题。 使用 Get-Help cmdlet 显示脚本和函数的帮助主题。

若要显示有关某个函数的帮助，请键入“get-help”，后跟函数名称。 例如，若要获取有关 Disable-PSRemoting 函数的帮助，请键入：

```
get-help disable-psremoting
```

若要显示有关某个脚本的帮助，请键入该脚本文件的完整限定路径。 如果脚本位于 Path 环境变量中列出的路径中，你可以在命令中省略路径。

例如，如果名为“TestScript.ps1”的脚本位于 C:\PS-Test 库中，若要显示有关该脚本的帮助主题，请键入：

```
get-help c:\ps-test\TestScript.ps1
```

用于显示 cmdlet 帮助的参数，如 *Detailed**Full**Examples* 和 *Parameter* 也适用于脚本帮助和函数帮助。 但是，当你通过键入“get-help”显示所有帮助时，将不显示有关函数和脚本的帮助。

有关为函数和脚本编写帮助的信息，请参阅 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)、[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 和 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)。

## 在线获取帮助
如果已经连接到 Internet，获取帮助的最好方法之一就是在线查看帮助主题。 由于在线主题易于更新，所以它们倾向于提供最新内容。

若要在线获取帮助，请尝试使用 Get-Help cmdlet 的 *Online* 参数。 Get-Help cmdlet 的 *Online* 参数仅适用于 cmdlet 帮助、函数帮助和脚本帮助。 不能将 *Online* 参数用于概念（关于）主题或提供程序帮助主题。 此外，由于这是一个可选功能，所以它并不适用于每一个 cmdlet、函数或脚本帮助主题。

但是，Windows PowerShell 附带的所有帮助主题（包括提供程序帮助和概念（有关）帮助主题）均在 Microsoft TechNet 库的 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 部分中在线提供。

若要使用 Get-Help cmdlet 的 *Online* 参数，请使用下列命令格式。

```
get-help <command-name> -online
```

例如，若要获取有关 Get-ChildItem cmdlet 的帮助主题的在线版本，请键入：

```
get-help get-childitem -online
```

如果该帮助主题有在线版本可用，则将在你的默认浏览器中打开它。

如果该帮助主题支持在线帮助，则你也可以查看该帮助主题的 Internet 地址 (URL)。 Internet 地址将显示在帮助主题的“相关链接”部分中。

例如，若要查看 Add-Computer cmdlet 的在线版本的 URL，请键入：

```
get-help add-computer
```

该主题的“相关链接”的第一行如下所示。

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

有关如何为帮助主题提供在线支持的信息，请参阅 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) 和 MSDN（Microsoft 开发人员网络）库中的“如何编写 Cmdlet 帮助”([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415))。

## 另请参阅
[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
[about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)



<!--HONumber=May16_HO2-->


