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
# <a name="editing-reference-articles"></a><span data-ttu-id="8c347-103">编辑参考文章</span><span class="sxs-lookup"><span data-stu-id="8c347-103">Editing reference articles</span></span>

<span data-ttu-id="8c347-104">Cmdlet 参考文章具有特定结构。</span><span class="sxs-lookup"><span data-stu-id="8c347-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="8c347-105">此结构是由 [PlatyPS][] 定义的。</span><span class="sxs-lookup"><span data-stu-id="8c347-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="8c347-106">PlatyPS 在 Markdown 中为 PowerShell 模块生成 cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="8c347-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="8c347-107">编辑 Markdown 文件后，使用 PlatyPS 创建 `Get-Help` cmdlet 使用的 MAML 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="8c347-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="8c347-108">PlatyPS 拥有针对 cmdlet 参考的硬编码架构，该架构已写入代码。</span><span class="sxs-lookup"><span data-stu-id="8c347-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="8c347-109">[platyPS.schema.md][] 文档尝试描述此结构。</span><span class="sxs-lookup"><span data-stu-id="8c347-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="8c347-110">架构冲突会导致生成错误，必须先修复这些错误，我们才能接受你参与撰写。</span><span class="sxs-lookup"><span data-stu-id="8c347-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="8c347-111">一般性指导</span><span class="sxs-lookup"><span data-stu-id="8c347-111">General guidelines</span></span>

- <span data-ttu-id="8c347-112">不要删除任何标头结构。</span><span class="sxs-lookup"><span data-stu-id="8c347-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="8c347-113">PlatyPS 需要一组特定的标头。</span><span class="sxs-lookup"><span data-stu-id="8c347-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="8c347-114">“输入类型”和“输出类型”标头必须包含一种类型。  </span><span class="sxs-lookup"><span data-stu-id="8c347-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="8c347-115">若 cmdlet 不接受输入或不返回值，则使用值 `None`。</span><span class="sxs-lookup"><span data-stu-id="8c347-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="8c347-116">仅[示例](#structuring-examples)部分允许隔离代码块。</span><span class="sxs-lookup"><span data-stu-id="8c347-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="8c347-117">内联代码跨度可用于任何段落。</span><span class="sxs-lookup"><span data-stu-id="8c347-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="8c347-118">设置 About_ 文件的格式</span><span class="sxs-lookup"><span data-stu-id="8c347-118">Formatting About_ files</span></span>

<span data-ttu-id="8c347-119">现在 `About_*` 文件由 [Pandoc][] 处理，而非 PlatyPS。</span><span class="sxs-lookup"><span data-stu-id="8c347-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="8c347-120">设置 `About_*` 文件的格式，以使其在 PowerShell 的所有版本上均可与发布工具良好兼容。</span><span class="sxs-lookup"><span data-stu-id="8c347-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="8c347-121">格式设置基本准则：</span><span class="sxs-lookup"><span data-stu-id="8c347-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="8c347-122">将行限制为 80 个字符</span><span class="sxs-lookup"><span data-stu-id="8c347-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="8c347-123">代码块和表限制为 76 个字符，因为将其转换为纯文本时 Pandoc 会将它们缩进四个空格</span><span class="sxs-lookup"><span data-stu-id="8c347-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="8c347-124">表需要在 76 个字符内</span><span class="sxs-lookup"><span data-stu-id="8c347-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="8c347-125">手动包装多个行中单元格的内容</span><span class="sxs-lookup"><span data-stu-id="8c347-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="8c347-126">在每行上使用开始和结束 `|` 字符</span><span class="sxs-lookup"><span data-stu-id="8c347-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="8c347-127">请参阅 [about_Comparison_Operators][about-example] 中的工作示例</span><span class="sxs-lookup"><span data-stu-id="8c347-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="8c347-128">使用 Pandoc 特殊字符 `\`、`$` 和 `<`</span><span class="sxs-lookup"><span data-stu-id="8c347-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="8c347-129">在标头中，必须使用前导 `\` 字符对这些字符进行转义，或者将这些字符括在反引号 (`` ` ``) 中</span><span class="sxs-lookup"><span data-stu-id="8c347-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="8c347-130">在段落中，应将这些字符置于代码跨度内。</span><span class="sxs-lookup"><span data-stu-id="8c347-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="8c347-131">例如：</span><span class="sxs-lookup"><span data-stu-id="8c347-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="8c347-132">结构示例</span><span class="sxs-lookup"><span data-stu-id="8c347-132">Structuring examples</span></span>

<span data-ttu-id="8c347-133">在 PlatyPS 架构中，EXAMPLES 标头是 H2 标头，每个示例是 H3 标头。 </span><span class="sxs-lookup"><span data-stu-id="8c347-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="8c347-134">在示例中，此架构不允许通过段落来分隔代码块。</span><span class="sxs-lookup"><span data-stu-id="8c347-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="8c347-135">支持的架构为：</span><span class="sxs-lookup"><span data-stu-id="8c347-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="8c347-136">为每个示例编号，并添加简短标题。</span><span class="sxs-lookup"><span data-stu-id="8c347-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="8c347-137">例如：</span><span class="sxs-lookup"><span data-stu-id="8c347-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="8c347-138">示例 1：获取 cmdlet、函数和别名</span><span class="sxs-lookup"><span data-stu-id="8c347-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="8c347-139">此命令将获取安装在计算机上的 PowerShell cmdlet、函数和别名。</span><span class="sxs-lookup"><span data-stu-id="8c347-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="8c347-140">示例 2：获取当前会话中的命令</span><span class="sxs-lookup"><span data-stu-id="8c347-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="8c347-141">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8c347-141">Next steps</span></span>

[<span data-ttu-id="8c347-142">编辑清单</span><span class="sxs-lookup"><span data-stu-id="8c347-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org
