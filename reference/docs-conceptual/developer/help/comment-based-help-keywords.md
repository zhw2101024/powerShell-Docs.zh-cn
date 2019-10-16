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
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361356"
---
# <a name="comment-based-help-keywords"></a>基于注释的帮助关键字

本主题列出并描述了基于注释的帮助中的关键字。

## <a name="keywords-in-comment-based-help"></a>基于注释的帮助中的关键字

下面是有效的基于注释的帮助关键字。 它们按其在帮助主题中通常出现的顺序列出，以及它们的预期用途。 这些关键字可以在基于注释的帮助中以任意顺序出现，它们不区分大小写。

请注意，@no__t 0 关键字优先于所有其他基于注释的帮助关键字。 如果 `.ExternalHelp` 存在，则[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet 不会显示基于注释的帮助，即使找不到与关键字的值匹配的帮助文件也是如此。

`.Synopsis` 对函数或脚本的简短说明。 每个主题中只能使用一次此关键字。

`.Description` 对函数或脚本的详细说明。 每个主题中只能使用一次此关键字。

`.Parameter` *@no__t >* 参数说明。 可以在函数或脚本中包含每个参数的 `.Parameter` 关键字。

@No__t-0 关键字可以在注释块中以任意顺序出现，但参数在 `Param` 语句或函数声明中的显示顺序决定了参数在帮助主题中的显示顺序。 若要更改帮助主题中参数的顺序，请更改 `Param` 语句或函数声明中参数的顺序。

还可以通过将注释放在参数变量名称之前的 `Param` 语句中来指定参数说明。 如果同时使用 @no__t 0 语句注释和 `.Parameter` 关键字，则使用与 `.Parameter` 关键字关联的说明，并忽略 @no__t 3 语句注释。

`.Example` 一个使用函数或脚本的示例命令，可选择后跟示例输出和说明。 为每个示例重复此关键字。

`.Inputs` 可通过管道传递给函数或脚本的对象 Microsoft .NET 框架类型。 还可以包括对输入对象的描述。

@no__t cmdlet 返回的对象 .NET Framework 类型。 还可以包括返回对象的描述。

@no__t 有关函数或脚本的附加信息。

`.Link` 相关主题的名称。 为每个相关主题重复此关键字。 此内容显示在帮助主题的 "相关链接" 部分中。

@No__t 的关键字内容还可以包含统一资源标识符（URI）到同一个帮助主题的联机版本。 当你使用 Get-help 的 @no__t 0 参数时，将打开联机版本。 URI 必须以 "http" 或 "https" 开头。

@no__t 函数或脚本使用或与之相关的技术或功能，则为0。 当 Get-help 命令包含 Get-help 的 `Component` 参数时，将显示此内容。

@no__t "帮助" 主题的用户角色。 当 Get-help 命令包含 Get-help 的 `Role` 参数时，将显示此内容。

`.Functionality`，此函数的预期用途。 当 Get-help 命令包含 Get-help 的 `Functionality` 参数时，将显示此内容。

`.ForwardHelpTargetName` `<Command-Name>` 将重定向到指定命令的帮助主题。 您可以将用户重定向到任何帮助主题，包括函数、脚本、cmdlet 或提供程序的帮助主题。

`.ForwardHelpCategory` @no__t 指定 ForwardHelpTargetName 中项的帮助类别。 有效值为 Alias、Cmdlet、提供程序、函数、提供程序、常规、FAQ、术语表、ScriptCommand、ExternalScript、筛选器或全部。 当存在具有相同名称的命令时，请使用此关键字避免冲突。

`.RemoteHelpRunspace` `<PSSession-variable>` 指定包含帮助主题的会话。 输入包含 PSSession 的变量。 @No__t cmdlet 使用此关键字查找导出的命令的帮助主题。

`.ExternalHelp` @no__t 为脚本或函数指定基于 XML 的帮助文件的路径和/或名称。

@No__t 的关键字告诉[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet 获取有关基于 XML 的文件中的脚本或函数的帮助。 **。** 对于脚本或函数使用基于 XML 的帮助文件时，需要使用 .externalhelp 关键字。 如果没有该函数，@no__t 将找不到该函数或脚本的帮助文件。

@No__t 关键字优先于所有其他基于注释的帮助关键字。 如果 `.ExternalHelp` 存在，则[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet 不会显示基于注释的帮助，即使找不到与关键字的值匹配的帮助文件也是如此。

当函数由脚本模块导出时，@no__t 值0应为不带路径的文件名。 `Get-Help` 在模块目录的特定于区域设置的子目录中查找文件。 不需要文件名，但最佳做法是使用以下文件名格式： `<ScriptModule>.psm1-help.xml`。

如果该函数未与模块相关联，则在的值中包含路径和文件名 **.Externalhelp**关键字。 如果 XML 文件的指定路径包含特定于 UI 区域性的子目录，`Get-Help` 会按照为 Windows 建立的语言回退标准，以递归方式搜索包含脚本或函数名称的 XML 文件的子目录。，就像对于所有基于 XML 的帮助主题那样。

有关 cmdlet 帮助基于 XML 的帮助文件格式的详细信息，请参阅[编写 Windows PowerShell Cmdlet 帮助](./writing-help-for-windows-powershell-cmdlets.md)。