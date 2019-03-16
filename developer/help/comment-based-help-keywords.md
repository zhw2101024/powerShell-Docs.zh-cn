---
title: 基于注释的帮助关键字 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058073"
---
# <a name="comment-based-help-keywords"></a>基于注释的帮助关键字

本主题列出并描述中基于注释的帮助关键字。

## <a name="keywords-in-comment-based-help"></a>中基于注释的帮助的关键字

以下是有效的基于注释的帮助关键字。 它们通常出现在其预期用途以及帮助主题中的顺序列出。 这些关键字可以出现在任何顺序的基于注释的帮助信息，并且不区分大小写。

请注意，`.ExternalHelp`关键字将优先于所有其他基于注释的帮助关键字。 当`.ExternalHelp`存在，则[Microsoft.PowerShell.Commands.Get 帮助](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 不显示基于注释的帮助，即使它找不到匹配关键字的值的帮助文件。

`.Synopsis` 函数或脚本的简短说明。 每个主题中，可以一次使用此关键字。

`.Description` 函数或脚本的详细的说明。 每个主题中，可以一次使用此关键字。

`.Parameter` *\<参数名称 >* 参数的说明。 可以包括`.Parameter`函数或脚本中每个参数的关键字。

`.Parameter`关键字可以出现在注释块中，按任何顺序，但参数中的显示的顺序`Param`语句或函数声明确定参数帮助主题中的显示的顺序。 若要更改帮助主题中的参数的顺序，更改参数的顺序`Param`语句或函数声明。

此外可以通过将放置的注释中指定参数说明`Param`参数变量名之前的语句。 如果同时使用这两者`Param`语句注释和一个`.Parameter`关键字，与关联的说明`.Parameter`使用关键字，和`Param`语句注释将被忽略。

`.Example` 使用函数或脚本，可以选择后跟示例输出和说明的示例命令。 对于每个示例中重复此关键字。

`.Inputs` 可以通过管道传递给函数或脚本的对象的 Microsoft.NET Framework 类型。 此外可以包含输入对象的说明。

`.Outputs` 该 cmdlet 返回的对象的.NET Framework 类型。 此外可以包含返回的对象的说明。

`.Notes` 有关函数或脚本的其他信息。

`.Link` 相关主题的名称。 每个相关主题的重复此关键字。 此内容将显示在帮助主题的相关链接部分。

`.Link`关键字内容还包括到相同的帮助主题的联机版本统一资源标识符 (URI)。 当你使用时，会打开联机版本`Online`参数获取帮助。 URI 必须以"http"或"https"开头。

`.Component` 技术或功能的函数或脚本使用，或与相关。 此内容的显示时的 Get-help 命令包括`Component`参数获取帮助。

`.Role` 用户角色的帮助主题。 此内容的显示时的 Get-help 命令包括`Role`参数获取帮助。

`.Functionality` 函数的预期的用法。 此内容的显示时的 Get-help 命令包括`Functionality`参数获取帮助。

`.ForwardHelpTargetName` `<Command-Name>` 重定向到指定的命令的帮助主题。 可以将用户重定向到任何帮助主题，包括函数、 脚本、 cmdlet 或提供程序的帮助主题。

`.ForwardHelpCategory` `<Category>` ForwardHelpTargetName 中指定的项的帮助类别。 有效值为别名、 Cmdlet、 HelpFile、 函数、 提供程序、 常规、 常见问题解答、 术语表、 脚本命令、 ExternalScript、 筛选器，或所有。 使用此关键字具有相同名称的命令时避免冲突。

`.RemoteHelpRunspace` `<PSSession-variable>` 指定包含帮助主题的会话。 输入包含 PSSession 的变量。 通过使用此关键字`Export-PSSession`cmdlet 查找导出的命令的帮助主题。

`.ExternalHelp` `<XML Help File>` 指定的路径和/或基于 XML 的帮助文件的脚本或函数的名称。

`.ExternalHelp`关键字告知[Microsoft.PowerShell.Commands.Get 帮助](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 来获取帮助的脚本或函数的基于 XML 的文件中。 **。ExternalHelp**关键字时是必需的脚本或函数中使用基于 XML 的帮助文件。 如果没有它，`Get-Help`将不到为该函数或脚本的帮助文件。

`.ExternalHelp`关键字将优先于所有其他基于注释的帮助关键字。 当`.ExternalHelp`存在，则[Microsoft.PowerShell.Commands.Get 帮助](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 不显示基于注释的帮助，即使它找不到匹配关键字的值的帮助文件。

该函数通过脚本模块的值的导出时`.ExternalHelp`应该是不含路径的文件名称。 `Get-Help` 查找在模块目录的区域设置特定的子目录中的文件。 没有任何要求的文件名称，但最佳做法是使用以下文件名称格式： `<ScriptModule>.psm1-help.xml`。

如果此函数不是与模块关联的值中包括的路径和文件名称 **。ExternalHelp**关键字。 如果指定的 XML 文件的路径包含 UI 区域性特定的子目录， `Get-Help` XML 文件同名的脚本或函数根据为建立回退标准的语言的子目录以递归方式搜索Windows，因为它会为所有基于 XML 的帮助主题。

有关 cmdlet 的帮助 XML 基于帮助文件格式的详细信息，请参阅[编写 Windows PowerShell Cmdlet 帮助](./writing-help-for-windows-powershell-cmdlets.md)。