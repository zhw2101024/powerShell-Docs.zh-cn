---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Tab 键扩展
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67031006"
---
# <a name="using-tab-expansion"></a>使用 Tab 键扩展

Command-line Shell 通常提供一种方法来自动完成长文件或命令的名称，从而加快命令输入并给出提示。 使用 PowerShell，可通过按 Tab 键来填充文件名和 cmdlet 名称<kbd></kbd>。

> [!NOTE]
> Tab 键扩展由内部函数 TabExpansion 或 TabExpansion2 控制。 由于此函数可被修改或覆盖，所以此讨论可用作针对默认 PowerShell 配置的行为的指导。

若要从可用选择中自动填充文件名或路径，键入部分名称并按下 <kbd>Tab</kbd> 键。 PowerShell 会自动将名称扩展至找到的第一个匹配项。 重复按下 <kbd>Tab</kbd> 将循环浏览所有可用选择。

cmdlet 名称的选项卡扩展稍有不同。 若要在 cmdlet 名称上使用选项卡扩充，键入名称的整个第一部分（即谓词），然后是后跟的连字符。 你可以填入名称的更多内容以进行部分匹配。 例如，如果键入 `get-co` 然后按 Tab 键，PowerShell 会自动将其扩展为 `Get-Command` cmdlet（注意，还会将字母的大小写改为标准形式）<kbd></kbd>。 如果再次按 Tab 键，PowerShell 会将此替换为另一个唯一匹配的 cmdlet 名称 `Get-Content`<kbd></kbd>。

你可以在同一行上重复使用 Tab 键扩展。 例如，可以通过输入以下内容在 `Get-Content` cmdlet 的名称上使用 tab 扩展：

```
PS> Get-Con<Tab>
```

当你按下 <kbd>Tab</kbd> 键时，该命令扩展为：

```
PS> Get-Content
```

然后你可以部分指定“智能安装”日志文件的路径并再次使用选项卡扩展：

```
PS> Get-Content c:\windows\acts<Tab>
```

当你按下 <kbd>Tab</kbd> 键时，该命令扩展为：

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Tab 键扩展进程的一个限制是 Tab 键始终解释为尝试完成单词。 如果将命令示例复制并粘贴到 PowerShell 控制台，请确保该示例不包含 Tab 键；如果包含 Tab 键，则结果将不可预测并且几乎不会得到预期的结果。
