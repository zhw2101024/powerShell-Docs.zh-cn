---
title: 编辑参考文章
description: 本文说明编辑 PowerShell 文档中的 cmdlet 参考和“关于”主题的特定要求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3c6f1b4fc27ca8ece7ec30317daf4ed2a6bc9228
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060322"
---
# <a name="editing-reference-articles"></a>编辑参考文章

Cmdlet 参考文章具有特定结构。 此结构是由 [PlatyPS][] 定义的。
PlatyPS 在 Markdown 中为 PowerShell 模块生成 cmdlet 帮助。 编辑 Markdown 文件后，使用 PlatyPS 创建 `Get-Help` cmdlet 使用的 MAML 帮助文件。

PlatyPS 拥有针对 cmdlet 参考的硬编码架构，该架构已写入代码。 [platyPS.schema.md][] 文档尝试描述此结构。 架构冲突会导致生成错误，必须先修复这些错误，我们才能接受你参与撰写。

## <a name="general-guidelines"></a>一般性指导

- 不要删除任何标头结构。 PlatyPS 需要一组特定的标头。
- “输入类型”和“输出类型”标头必须包含一种类型。   若 cmdlet 不接受输入或不返回值，则使用值 `None`。
- 仅[示例](#structuring-examples)部分允许隔离代码块。
- 内联代码跨度可用于任何段落。

## <a name="formatting-about_-files"></a>设置 About_ 文件的格式

现在 `About_*` 文件由 [Pandoc][] 处理，而非 PlatyPS。 设置 `About_*` 文件的格式，以使其在 PowerShell 的所有版本上均可与发布工具良好兼容。

格式设置基本准则：

- 将行限制为 80 个字符
- 代码块和表限制为 76 个字符，因为将其转换为纯文本时 Pandoc 会将它们缩进四个空格
- 表需要在 76 个字符内
  - 手动包装多个行中单元格的内容
  - 在每行上使用开始和结束 `|` 字符
  - 请参阅 [about_Comparison_Operators][about-example] 中的工作示例
- 使用 Pandoc 特殊字符 `\`、`$` 和 `<`
  - 在标头中，必须使用前导 `\` 字符对这些字符进行转义，或者将这些字符括在反引号 (`` ` ``) 中
  - 在段落中，应将这些字符置于代码跨度内。 例如：

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a>结构示例

在 PlatyPS 架构中，EXAMPLES 标头是 H2 标头，每个示例是 H3 标头。 

在示例中，此架构不允许通过段落来分隔代码块。 支持的架构为：

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

为每个示例编号，并添加简短标题。

例如：

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>示例 1：获取 cmdlet、函数和别名

此命令将获取安装在计算机上的 PowerShell cmdlet、函数和别名。

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>示例 2：获取当前会话中的命令

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>后续步骤

[编辑清单](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org
