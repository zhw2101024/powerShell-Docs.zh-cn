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
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848103"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>编写 PowerShell 脚本和函数的帮助

当 PowerShell 脚本和函数与其他人共享时，它们应该是完整记录的。
Cmdlet 显示脚本和函数的帮助主题，其格式与显示 cmdlet 的帮助相同，并且所有`Get-Help`参数都适用于脚本和函数的帮助主题。 `Get-Help`

PowerShell 脚本可以包括有关脚本的帮助主题，以及有关脚本中每个函数的帮助主题。
独立于脚本共享的函数可以包含它们自己的帮助主题。

本文档介绍了 "帮助" 主题的格式和正确位置，并为内容提供指导原则。

## <a name="types-of-script-and-function-help"></a>脚本和函数帮助的类型

### <a name="comment-based-help"></a>基于注释的帮助
描述脚本或函数的帮助主题可作为脚本或函数中的一组注释实现。
为脚本编写基于注释的帮助和脚本中的函数时，请注意用于放置基于注释的帮助的规则。
此位置确定 cmdlet 是否`Get-Help`将帮助主题与脚本或函数关联。
有关编写基于注释的帮助主题的详细信息，请参阅[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

### <a name="xml-based-command-help"></a>基于 XML 的命令帮助
描述脚本或函数的帮助主题可以在使用 command help 架构的 XML 文件中实现。
若要将脚本或函数与 xml 文件相关联，请`ExternalHelp`使用 comment 关键字，后跟 xml 文件的路径和名称。

如果存在`Get-Help` `ExternalHelp` comment 关键字，则其优先于基于注释的帮助，即使找不到与关键字的值匹配的帮助文件也是如此。 `ExternalHelp`

### <a name="online-help"></a>联机帮助
你可以在 Internet 上发布帮助主题，然后直接`Get-Help`打开这些主题。
有关编写基于注释的帮助主题的详细信息，请参阅[支持联机帮助](../module/supporting-online-help.md)。

没有已建立的方法来编写脚本和函数的概念（"关于"）主题。
但是，你可以在 "命令帮助" 主题的 "相关链接" 部分中，在 Internet 上列出主题及其 Url。

## <a name="content-considerations-for-script-and-function-help"></a>脚本和函数帮助的内容注意事项

- 如果你正在编写一个非常简短的帮助主题，其中只包含几个可用的命令帮助部分，请确保包含脚本或函数参数的明确说明。 还在 "示例" 部分中包括一个或两个示例命令，即使您决定省略示例说明。

- 在所有说明中，请将命令作为脚本或函数引用。 此信息可帮助用户了解和管理命令。

  例如，下面的详细说明指出，新的主题命令是一个脚本。 这会提醒用户他们在运行时需要指定路径和全名。

  > "新的主题脚本为输入文件中的每个主题名称创建一个空白的概念主题 ..."

  下面是一个函数的`Disable-PSRemoting`详细说明状态。 当会话中包含多个具有相同名称的命令时，此信息对用户特别有用，其中有些命令可能由优先级较高的命令隐藏。

  > 此`Disable-PSRemoting`函数将禁用本地计算机上的所有会话配置 。

- 在脚本帮助主题中，介绍如何将该脚本作为一个整体使用。 如果你还在脚本中编写函数的帮助主题，请在脚本帮助主题的 "相关链接" 部分中提到函数帮助主题，并将其包含在脚本帮助主题中。 相反，当某个函数作为脚本的一部分时，将在函数帮助主题中介绍函数在脚本中所扮演的角色以及如何单独使用该函数。 然后在函数帮助主题的 "相关链接" 部分中列出脚本帮助主题。

- 编写脚本帮助主题的示例时，请确保在示例命令中包含脚本文件的路径。 这会提醒用户他们必须显式指定路径，即使脚本在当前目录中也是如此。

- 在函数帮助主题中，提醒用户此函数仅在当前会话中存在，若要在其他会话中使用它，需要添加它，或者将其添加到 PowerShell 配置文件。

- `Get-Help`仅当脚本文件和帮助主题文件保存到正确的位置时，才显示脚本或函数的帮助主题。 因此，在脚本或函数帮助主题中包含用于安装 PowerShell 或保存或安装脚本或函数的说明并不有用。 相反，请在用于分发脚本或函数的文档中包含任何安装说明。

## <a name="see-also"></a>另请参阅

[编写基于注释的帮助主题](./writing-comment-based-help-topics.md)
