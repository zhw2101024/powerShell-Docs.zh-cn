---
title: PowerShell-Docs 风格指南
description: 本文介绍用于撰写 PowerShell 文档的风格规则。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402574"
---
# <a name="powershell-docs-style-guide"></a>PowerShell-Docs 风格指南

本文介绍特定于 PowerShell-Docs 内容的风格指南。 本文是根据[概述](overview.md#get-started-writing-docs)中所述的信息撰写的。

## <a name="product-terminology"></a>产品术语

PowerShell 有多个变体。
下表定义了一些用于介绍 PowerShell 的不同术语。

- **PowerShell** - 这是默认名称。 我们认为 PowerShell 7 及其以后的版本将是真正的 PowerShell。

- **PowerShell Core** - 基于 .NET Core 生成的 PowerShell。 只有在有必要与 Windows PowerShell 进行区分的情况下，才会使用术语“Core”  。

- **Windows PowerShell** - 基于 .NET Framework 生成的 PowerShell。 Windows PowerShell 仅对 Windows 提供，并且需要完整的 Framework。

通常，可以将文档中对“Windows PowerShell”的引用更改为“PowerShell”。
在介绍 Windows 特定的技术时，不能更改“Windows PowerShell”  。

## <a name="markdown-specifics"></a>Markdown 详情

用于生成文档的 Microsoft 开放发布系统 (OPS) 使用 [markdig][] 处理 Markdown 文档。 Markdig 根据最新 [CommonMark][] 规范的规则分析文档。

新的 CommonMark 规范比某些 Markdown 元素的构造要严格得多。 请密切关注本文档中提供的详细信息。

### <a name="blank-lines-spaces-and-tabs"></a>空白行、空格和制表符

删除重复的空白行。 多个空白行在 HTML 中呈现为单个空白行，因此多个空白行不起作用。

在 Markdown 中，空白行还表示块的末尾。 在不同类型的 Markdown 块之间（例如，在段落和列表或标题之间）应该有一个空白行。

> [!NOTE]
> 间距在 Markdown 中非常重要。 始终使用空格而不是硬制表符。 删除行尾的多余空格。

### <a name="titles-and-headings"></a>标题

只使用 [ATX 标题][atx]（# 样式，不用 `=` 或 `-` 样式标题）。

- 使用句首大写形式 - 只对专有名词和标题的首个字母使用大写形式
- `#` 与标题的首个字母之间必须有一个空格
- 标题前后应该都留有一个空白行
- 每个文档只有 1 个 H1
- 标题级别应按 1 递增。 不要跨级
- 不要在标题中使用粗体或其他标记

### <a name="limit-line-length-to-100-characters"></a>将行长度限制为 100 个字符

这适用于概念性文章和 cmdlet 参考。 About_topics 限制为 80 个字符。
限制行长度可以改进 git diffs 和历史记录的可读性。 同时也便于其他作者参与撰写文档。

在 Visual Studio Code 中使用 [Reflow Markdown][reflow] 扩展可以轻松地重排段落以适应指定的行长度。

### <a name="lists"></a>列表

如果列表包含多个句子或段落，请考虑使用子级标题代替列表。

列表前后应该都留有一个空白行。

#### <a name="unordered-lists"></a>未排序列表

除非列表项包含多个句子，否则不要以句点结尾。 对于列表项项目符号，使用连字符 (`-`)。 这样可以避免与使用星号 [`*`] 的粗体或斜体标记混淆。 若要在项目符号项下添加段落或其他元素，请插入一个换行符，并使缩进与项目符号后的第一个字符对齐。

例如：

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

这是一个列表，其中包含项目符号项下的子元素。

- 第一个项目符号项

  说明第一个项目符号的句子。

  - 子项目符号项

    说明子项目符号的句子。

- 第二个项目符号项
- 第三个项目符号项

#### <a name="ordered-lists"></a>已排序列表

若要在带编号的项下添加段落或其他元素，请使缩进与项编号后的第一个字符对齐。 编号列表中的所有项均应使用数字 `1.`，而不是递增每个项的编号数字值。 Markdown 呈现会自动递增该值。 这使重新排序项目变得更加容易，并使下级内容的缩进标准化。

例如：

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

最终呈现的 Markdown 如下：

1. 对于第一个元素，在 1 之后插入一个空格。 长句应换行到下一行，并且必须与编号列表标记后的第一个字符对齐。

   若要包括第二个元素（如本例所示），请在第一个元素后插入一个换行符，并对齐缩进。 第二个元素的缩进必须与编号列表标记后的第一个字符对齐。 对于这样的一位数的项，缩进到第 4 列。 对于两位数的项（例如项编号 10），缩进到第 5 列。

1. 下一个带编号的项从此处开始。

### <a name="formatting-command-syntax-elements"></a>设置命令语法元素格式

- 始终对 cmdlet 和参数使用全名。 避免使用别名，除非专门演示别名。

- 在段落中，语言关键字、cmdlet 名称、变量和文件路径都应使用反引号 (`` ` ``) 字符引起来。 属性、参数和类名称应为粗体  。

  例如：

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- 通过名称引用参数时，名称应为粗体  。 在说明如何使用带有连字符前缀的参数时，应使用反引号将参数引起来。 例如：

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- 引用外部命令（EXE、脚本等）时，命令名称应为粗体、全部小写（如果位于句子开头，则为大写），并加上相应的文件扩展名。 例如：

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- 显示外部命令的示例用法时，应使用反引号将示例引起来。
  如果名称与别名冲突，必须在命令示例中加上文件扩展名。 例如：

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- 在撰写概念性文章（而不是参考内容）时，应将 cmdlet 名称的第一个实例超链接到 cmdlet 文档。 不要在超链接的括号内使用反引号、粗体或其他标记。

  例如：

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  有关详细信息，请参阅本文中的[超链接](#hyperlinks)一节。

### <a name="images"></a>映像

用于添加图像的语法如下：

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

其中 `alt text` 是图像的简要说明，`<folder path>` 是图像的相对路径。 必须为视觉障碍人士的屏幕阅读器使用替代文本。 如果存在无法呈现图像的站点 bug，则此方法也非常有用。

图像应存储在包含文章的文件夹内的 `media/<article-name>` 文件夹中。
不应在文章之间共享图像。 在 `media` 文件夹下创建一个与你的文章的文件名匹配的文件夹。 将该文章的图像复制到新文件夹。 如果有多篇文章使用了同一个图像，则每个图像文件夹都必须包含该图像文件的副本。 这种做法可以防止一篇文章中的图像更改影响另一篇文章。

支持以下图像文件类型：`*.png`、`*.gif`、`*.jpeg`、`*.jpg`、`*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>开放发布系统支持的 Markdown 扩展

[Microsoft Docs 创作包](/contribute/how-to-write-docs-auth-pack)中包含支持发布系统独有功能的工具。 “通知”是一种 Markdown 扩展，用于创建在 docs.microsoft.com 上呈现的块引用，这些内容带有可指示内容重要性的颜色和图标。 支持以下通知类型：

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

这些通知在 docs.microsoft.com 上看起来如下所示：

> [!NOTE]
> 即使略读，用户也应注意的信息。

> [!TIP]
> 为用户带来更大成就感的可选信息。

> [!IMPORTANT]
> 用户成功所需的基本信息。

> [!CAUTION]
> 操作的潜在不良后果。

> [!WARNING]
> 操作的某些危险后果。

## <a name="hyperlinks"></a>超链接

- 避免使用裸 URL。 链接应使用 Markdown 语法 `[friendlyname](url-or-path)`
- 必要时可以使用裸 URL，但应使用反引号引起来。 例如：

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- URL 链接应尽可能使用 HTTPS。
- 链接必须具有友好名称，通常是链接主题的标题
- 底部“相关链接”部分中的所有项都应具有超链接。
- 不要在超链接的括号内使用反引号、粗体或其他标记。

### <a name="linking-to-other-content"></a>链接到其他内容

发布系统支持两种类型的超链接：URL 和文件链接。

URL 链接可以是相对于 docs.microsoft.com 根的 URL 路径。 也可以是包含完整 URL 语法的绝对 URL。 （例如：`https:/github.com/MicrosoftDocs/PowerShell-Docs`）

- 链接到 PowerShell-Docs 之外的内容时，或在 PowerShell-docs 内的 cmdlet 参考与概念性文章之间链接时，请使用 URL 链接。
- 链接创建相对链接的最简单方法是从浏览器复制 URL，然后从粘贴到 Markdown 的值中删除 `https://docs.microsoft.com/en-us`。
   - 不要在 Microsoft 属性的 URL 中包含区域设置（例如， 请从 URL 中删除“/en-us”）。
- 指向外部网站的所有 URL 都应使用 HTTPS（除非对目标站点无效）。

从一个参考文章链接到另一个参考文章，或从一个概念性文章链接到另一个概念性文章时，使用文件链接。 如果需要链接到特定版本的 PowerShell 的参考文章，则需要使用 URL 链接。

- 文件链接包含相对文件路径（例如：`../folder/file.md`）
- 所有文件路径都使用正斜杠 (`/`) 字符

## <a name="formatting-code-samples"></a>设置代码示例格式

Markdown 支持两种不同的代码样式：

- 代码范围（内联）- 用单个反引号 (`` ` ``) 字符标记。 在段落中使用，而不是作为独立的块使用。
- 代码块 - 使用三个反引号 (`` ``` ``) 字符串引起来的多行代码块。 代码块的反引号后面还可能跟有一个语言标签。 语言标签使代码块内容的语法突出显示。

### <a name="using-code-blocks"></a>使用代码块

Markdown 允许以缩进方式表示代码块，但这种模式可能会出现问题，应避免使用此模式。 所有代码块都应包含在代码隔离区中。 代码隔离区是由三个反引号 (`` ``` ``) 字符串引起来的代码块。 代码隔离区标记必须位于代码示例前后其自己的行上。 代码块开头的标记可能具有可选的语言标签。 Microsoft 的开放发布系统 (OPS) 使用语言标签来支持语法突出显示功能。

OPS 还添加了可将代码块的内容复制到剪贴板的“复制”按钮  。 这样，你就可以将代码快速粘贴到脚本中，以测试代码示例。 但是，并非文档中的所有示例都应该以这种方式运行。 一些代码块是 PowerShell 概念的简单说明。

文档中使用两种类型的代码块：

1. 说明性示例
2. 可执行示例

### <a name="syntax-code-blocks"></a>语法代码块

此示例演示 `Get-Command` cmdlet 所有可能的参数。

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

此示例以通用术语描述 `for` 语句：

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>说明性示例

说明性示例用于解释 PowerShell 概念。 不应将它们复制到剪贴板来执行。 这些示例最常用于易于键入的简单示例。
它们还用于演示命令语法的语法示例。 代码块可能包含所演示命令的示例输出。

以下简单示例演示 PowerShell 比较运算符：

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

请注意，此示例提供简化的 PowerShell 提示，并显示生成的输出。 在这种情况下，我们不希望读者复制并运行此示例。

### <a name="executable-examples"></a>可执行示例

更复杂的示例或应该便于复制和执行的示例应使用以下块样式标记：

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

PowerShell 命令显示的输出应包含在 Output 代码块中，以防止语法突出显示  。 例如：

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

Output 代码标签不是语法突出显示系统支持的一种正式“语言”  。
但是，此标签非常有用，因为 OPS 会将“Output”标签添加到网页上的代码框框架中。 “Output”代码框不会突出显示语法。

## <a name="coding-style-rules"></a>编码样式规则

### <a name="avoid-line-continuation-in-code-samples"></a>避免在代码示例中出现续行符

避免在 PowerShell 代码示例中使用续行符 (`` ` ``)。 如果行尾出现多余的空格，会很难看到续行符，并且可能会引发问题。

- 使用 PowerShell 展开来缩短包含大量参数的 cmdlet 的行长度。
- 利用 PowerShell 的自然换行机会，如竖线 (`|`) 字符、左大括号、圆括号和方括号之后。

### <a name="avoid-using-powershell-prompts-in-examples"></a>避免在示例中使用 PowerShell 提示

不建议使用提示字符串，应该将其限制在旨在说明命令行用法的方案。 对于其中大多数示例，提示字符串应为 `PS>`。 此提示与特定于 OS 的指示器无关。

如果示例演示改变提示的命令，或显示的路径对所演示的方案非常重要时，则需要提示。 下面的示例演示使用注册表提供程序时提示的变化。

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a>请勿在示例中使用别名

应始终使用所有 cmdlet 和参数的全名，除非专门讨论别名。 Cmdlet 和参数名称必须使用代码中定义的正确拼写。

### <a name="using-parameters-in-examples"></a>在示例中使用参数

避免使用位置参数。 通常，即使是位置参数，也应始终在示例中包含参数名称。 这样可以减少在示例中产生混淆的可能性。

## <a name="next-steps"></a>后续步骤

[编辑 cmdlet 参考](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
