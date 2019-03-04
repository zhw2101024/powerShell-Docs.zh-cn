---
title: 编写 PowerShell 脚本和函数的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857473"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>编写 PowerShell 脚本和函数的帮助

PowerShell 脚本和函数应完整记录时与其他人共享。
`Get-Help` Cmdlet 显示脚本和函数的帮助主题中的相同的格式显示有关 cmdlet 和的所有帮助的方式`Get-Help`参数对脚本和函数的帮助主题的工作。

PowerShell 脚本可以在脚本中包括有关脚本的帮助主题以及有关每个函数的帮助主题。
独立于脚本共享的函数可以包含其自己的帮助主题。

本文档介绍了格式和正确放置的帮助主题，并建议内容的指导原则。

## <a name="types-of-script-and-function-help"></a>类型的脚本和函数帮助

### <a name="comment-based-help"></a>基于注释的帮助
介绍脚本或函数的帮助主题可以实现为一系列脚本或函数内的注释。
当在脚本中编写的脚本和函数基于注释的帮助，请注意规则放置基于注释的帮助。
放置将确定是否`Get-Help`cmdlet 将脚本或函数与相关联的帮助主题。
有关编写基于注释的帮助主题的详细信息，请参阅[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

### <a name="xml-based-command-help"></a>基于 XML 的命令的帮助
可以在使用命令帮助架构的 XML 文件中实现介绍脚本或函数的帮助主题。
若要将脚本或函数相关联的 XML 文件，请使用`ExternalHelp`注释关键字后面的路径和 XML 文件的名称。

当`ExternalHelp`注释关键字是否存在，它将优先于基于注释的帮助，即使`Get-Help`找不到匹配的值的帮助文件`ExternalHelp`关键字。

### <a name="online-help"></a>联机帮助
可以在 Internet 上发布您的帮助主题，然后将`Get-Help`打开主题。
有关编写基于注释的帮助主题的详细信息，请参阅[支持联机帮助](../module/supporting-online-help.md)。

没有已建立的方法以进行写入 （"关于"） 的脚本和函数的主题。
但是，您可以发布 Internet 列表上的概念性主题的主题，因此其 Url 命令的帮助主题的相关链接部分中。

## <a name="content-considerations-for-script-and-function-help"></a>脚本和函数的内容注意事项帮助

- 如果你正在使用只有几个可用命令的帮助部分编写非常简短的帮助主题，请务必包括脚本或函数参数的详细描述。 此外在示例部分中，包含一个或两个示例命令即使你决定以忽略此参数的示例说明。

- 在所有的说明，请参阅命令的访问权限的脚本或函数。 此信息可帮助用户了解和管理命令。

  例如，以下详细的说明指出新建主题命令是一个脚本。 这将提醒用户他们需要在运行时指定的路径和完整名称。

  > "新建主题脚本...在输入文件中创建空白的概念主题，为每个主题名称"

  下面详细的说明指出`Disable-PSRemoting`是一个函数。 此信息在会话中包括多个命令具有相同的名称，其中一些可能被隐藏某一命令优先级更高时向用户特别有用。

  > `Disable-PSRemoting`函数可禁用本地计算机上的所有会话配置...

- 在脚本的帮助主题中，介绍如何使用此脚本作为一个整体。 如果您还会在脚本中编写函数的帮助主题，提到您脚本的帮助主题中的函数和脚本帮助主题的相关链接部分中包括对函数的帮助主题。 相反，如果函数是脚本的一部分，阐释函数帮助主题中该函数在脚本和它可以如何使用独立中所扮演的角色。 然后列出函数帮助主题的相关链接部分中的脚本帮助主题。

- 在编写脚本的帮助主题的示例，请务必在示例命令中包含的脚本文件的路径。 这将提醒用户他们都必须显式指定的路径，即使脚本位于当前目录。

- 在函数的帮助主题中，提醒用户，仅在当前会话中存在的函数，若要在其他会话中使用它，他们需要添加它，或将其添加 PowerShell 配置文件。

- `Get-Help` 仅当在正确的位置保存的脚本文件和帮助主题文件时将显示有关脚本或函数的帮助主题。 因此，不需要包含有关安装 PowerShell，或保存或安装脚本或函数的帮助主题中的脚本或函数的说明。 相反，包括用于分发的脚本或函数的文档中的任何安装说明。

## <a name="see-also"></a>另请参阅

 [编写脚本和函数的基于 XML 的帮助主题](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [命令为编写基于 XML 的帮助主题](./writing-xml-based-help-topics-for-commands.md)

 [编写基于注释的帮助主题](./writing-comment-based-help-topics.md)
