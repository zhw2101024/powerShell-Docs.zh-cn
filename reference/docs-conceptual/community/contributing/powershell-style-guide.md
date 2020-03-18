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
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="6f6c5-103">PowerShell-Docs 风格指南</span><span class="sxs-lookup"><span data-stu-id="6f6c5-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="6f6c5-104">本文介绍特定于 PowerShell-Docs 内容的风格指南。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="6f6c5-105">本文是根据[概述](overview.md#get-started-writing-docs)中所述的信息撰写的。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="6f6c5-106">产品术语</span><span class="sxs-lookup"><span data-stu-id="6f6c5-106">Product Terminology</span></span>

<span data-ttu-id="6f6c5-107">PowerShell 有多个变体。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="6f6c5-108">下表定义了一些用于介绍 PowerShell 的不同术语。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="6f6c5-109">**PowerShell** - 这是默认名称。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="6f6c5-110">我们认为 PowerShell 7 及其以后的版本将是真正的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="6f6c5-111">**PowerShell Core** - 基于 .NET Core 生成的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="6f6c5-112">只有在有必要与 Windows PowerShell 进行区分的情况下，才会使用术语“Core”  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="6f6c5-113">**Windows PowerShell** - 基于 .NET Framework 生成的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="6f6c5-114">Windows PowerShell 仅对 Windows 提供，并且需要完整的 Framework。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="6f6c5-115">通常，可以将文档中对“Windows PowerShell”的引用更改为“PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="6f6c5-116">在介绍 Windows 特定的技术时，不能更改“Windows PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="6f6c5-117">Markdown 详情</span><span class="sxs-lookup"><span data-stu-id="6f6c5-117">Markdown specifics</span></span>

<span data-ttu-id="6f6c5-118">用于生成文档的 Microsoft 开放发布系统 (OPS) 使用 [markdig][] 处理 Markdown 文档。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="6f6c5-119">Markdig 根据最新 [CommonMark][] 规范的规则分析文档。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="6f6c5-120">新的 CommonMark 规范比某些 Markdown 元素的构造要严格得多。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="6f6c5-121">请密切关注本文档中提供的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="6f6c5-122">空白行、空格和制表符</span><span class="sxs-lookup"><span data-stu-id="6f6c5-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="6f6c5-123">删除重复的空白行。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="6f6c5-124">多个空白行在 HTML 中呈现为单个空白行，因此多个空白行不起作用。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="6f6c5-125">在 Markdown 中，空白行还表示块的末尾。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="6f6c5-126">在不同类型的 Markdown 块之间（例如，在段落和列表或标题之间）应该有一个空白行。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="6f6c5-127">间距在 Markdown 中非常重要。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="6f6c5-128">始终使用空格而不是硬制表符。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="6f6c5-129">删除行尾的多余空格。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="6f6c5-130">标题</span><span class="sxs-lookup"><span data-stu-id="6f6c5-130">Titles and headings</span></span>

<span data-ttu-id="6f6c5-131">只使用 [ATX 标题][atx]（# 样式，不用 `=` 或 `-` 样式标题）。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="6f6c5-132">使用句首大写形式 - 只对专有名词和标题的首个字母使用大写形式</span><span class="sxs-lookup"><span data-stu-id="6f6c5-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="6f6c5-133">`#` 与标题的首个字母之间必须有一个空格</span><span class="sxs-lookup"><span data-stu-id="6f6c5-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="6f6c5-134">标题前后应该都留有一个空白行</span><span class="sxs-lookup"><span data-stu-id="6f6c5-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="6f6c5-135">每个文档只有 1 个 H1</span><span class="sxs-lookup"><span data-stu-id="6f6c5-135">Only one H1 per document</span></span>
- <span data-ttu-id="6f6c5-136">标题级别应按 1 递增。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-136">Header levels should increment by one.</span></span> <span data-ttu-id="6f6c5-137">不要跨级</span><span class="sxs-lookup"><span data-stu-id="6f6c5-137">Do not skip levels</span></span>
- <span data-ttu-id="6f6c5-138">不要在标题中使用粗体或其他标记</span><span class="sxs-lookup"><span data-stu-id="6f6c5-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="6f6c5-139">将行长度限制为 100 个字符</span><span class="sxs-lookup"><span data-stu-id="6f6c5-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="6f6c5-140">这适用于概念性文章和 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="6f6c5-141">About_topics 限制为 80 个字符。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="6f6c5-142">限制行长度可以改进 git diffs 和历史记录的可读性。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-142">Limiting the line length improves the readability git diffs and history.</span></span> <span data-ttu-id="6f6c5-143">同时也便于其他作者参与撰写文档。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="6f6c5-144">在 Visual Studio Code 中使用 [Reflow Markdown][reflow] 扩展可以轻松地重排段落以适应指定的行长度。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="6f6c5-145">列表</span><span class="sxs-lookup"><span data-stu-id="6f6c5-145">Lists</span></span>

<span data-ttu-id="6f6c5-146">如果列表包含多个句子或段落，请考虑使用子级标题代替列表。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="6f6c5-147">列表前后应该都留有一个空白行。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="6f6c5-148">未排序列表</span><span class="sxs-lookup"><span data-stu-id="6f6c5-148">Unordered lists</span></span>

<span data-ttu-id="6f6c5-149">除非列表项包含多个句子，否则不要以句点结尾。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="6f6c5-150">对于列表项项目符号，使用连字符 (`-`)。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="6f6c5-151">这样可以避免与使用星号 [`*`] 的粗体或斜体标记混淆。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="6f6c5-152">若要在项目符号项下添加段落或其他元素，请插入一个换行符，并使缩进与项目符号后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="6f6c5-153">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="6f6c5-154">这是一个列表，其中包含项目符号项下的子元素。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="6f6c5-155">第一个项目符号项</span><span class="sxs-lookup"><span data-stu-id="6f6c5-155">First bullet item</span></span>

  <span data-ttu-id="6f6c5-156">说明第一个项目符号的句子。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="6f6c5-157">子项目符号项</span><span class="sxs-lookup"><span data-stu-id="6f6c5-157">Sub-bullet item</span></span>

    <span data-ttu-id="6f6c5-158">说明子项目符号的句子。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="6f6c5-159">第二个项目符号项</span><span class="sxs-lookup"><span data-stu-id="6f6c5-159">Second bullet item</span></span>
- <span data-ttu-id="6f6c5-160">第三个项目符号项</span><span class="sxs-lookup"><span data-stu-id="6f6c5-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="6f6c5-161">已排序列表</span><span class="sxs-lookup"><span data-stu-id="6f6c5-161">Ordered lists</span></span>

<span data-ttu-id="6f6c5-162">若要在带编号的项下添加段落或其他元素，请使缩进与项编号后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="6f6c5-163">编号列表中的所有项均应使用数字 `1.`，而不是递增每个项的编号数字值。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="6f6c5-164">Markdown 呈现会自动递增该值。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="6f6c5-165">这使重新排序项目变得更加容易，并使下级内容的缩进标准化。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="6f6c5-166">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-166">For example:</span></span>

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

<span data-ttu-id="6f6c5-167">最终呈现的 Markdown 如下：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="6f6c5-168">对于第一个元素，在 1 之后插入一个空格。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="6f6c5-169">长句应换行到下一行，并且必须与编号列表标记后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="6f6c5-170">若要包括第二个元素（如本例所示），请在第一个元素后插入一个换行符，并对齐缩进。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="6f6c5-171">第二个元素的缩进必须与编号列表标记后的第一个字符对齐。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="6f6c5-172">对于这样的一位数的项，缩进到第 4 列。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="6f6c5-173">对于两位数的项（例如项编号 10），缩进到第 5 列。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="6f6c5-174">下一个带编号的项从此处开始。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="6f6c5-175">设置命令语法元素格式</span><span class="sxs-lookup"><span data-stu-id="6f6c5-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="6f6c5-176">始终对 cmdlet 和参数使用全名。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="6f6c5-177">避免使用别名，除非专门演示别名。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="6f6c5-178">在段落中，语言关键字、cmdlet 名称、变量和文件路径都应使用反引号 (`` ` ``) 字符引起来。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="6f6c5-179">属性、参数和类名称应为粗体  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="6f6c5-180">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="6f6c5-181">通过名称引用参数时，名称应为粗体  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="6f6c5-182">在说明如何使用带有连字符前缀的参数时，应使用反引号将参数引起来。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="6f6c5-183">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="6f6c5-184">引用外部命令（EXE、脚本等）时，命令名称应为粗体、全部小写（如果位于句子开头，则为大写），并加上相应的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="6f6c5-185">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="6f6c5-186">显示外部命令的示例用法时，应使用反引号将示例引起来。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="6f6c5-187">如果名称与别名冲突，必须在命令示例中加上文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="6f6c5-188">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="6f6c5-189">在撰写概念性文章（而不是参考内容）时，应将 cmdlet 名称的第一个实例超链接到 cmdlet 文档。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="6f6c5-190">不要在超链接的括号内使用反引号、粗体或其他标记。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="6f6c5-191">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="6f6c5-192">有关详细信息，请参阅本文中的[超链接](#hyperlinks)一节。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="6f6c5-193">映像</span><span class="sxs-lookup"><span data-stu-id="6f6c5-193">Images</span></span>

<span data-ttu-id="6f6c5-194">用于添加图像的语法如下：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="6f6c5-195">其中 `alt text` 是图像的简要说明，`<folder path>` 是图像的相对路径。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="6f6c5-196">必须为视觉障碍人士的屏幕阅读器使用替代文本。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="6f6c5-197">如果存在无法呈现图像的站点 bug，则此方法也非常有用。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="6f6c5-198">图像应存储在包含文章的文件夹内的 `media/<article-name>` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="6f6c5-199">不应在文章之间共享图像。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-199">Images should not be shared between articles.</span></span> <span data-ttu-id="6f6c5-200">在 `media` 文件夹下创建一个与你的文章的文件名匹配的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="6f6c5-201">将该文章的图像复制到新文件夹。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="6f6c5-202">如果有多篇文章使用了同一个图像，则每个图像文件夹都必须包含该图像文件的副本。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="6f6c5-203">这种做法可以防止一篇文章中的图像更改影响另一篇文章。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="6f6c5-204">支持以下图像文件类型：`*.png`、`*.gif`、`*.jpeg`、`*.jpg`、`*.svg`</span><span class="sxs-lookup"><span data-stu-id="6f6c5-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="6f6c5-205">开放发布系统支持的 Markdown 扩展</span><span class="sxs-lookup"><span data-stu-id="6f6c5-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="6f6c5-206">[Microsoft Docs 创作包](/contribute/how-to-write-docs-auth-pack)中包含支持发布系统独有功能的工具。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="6f6c5-207">“通知”是一种 Markdown 扩展，用于创建在 docs.microsoft.com 上呈现的块引用，这些内容带有可指示内容重要性的颜色和图标。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="6f6c5-208">支持以下通知类型：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="6f6c5-209">这些通知在 docs.microsoft.com 上看起来如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="6f6c5-210">即使略读，用户也应注意的信息。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="6f6c5-211">为用户带来更大成就感的可选信息。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f6c5-212">用户成功所需的基本信息。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="6f6c5-213">操作的潜在不良后果。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="6f6c5-214">操作的某些危险后果。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="6f6c5-215">超链接</span><span class="sxs-lookup"><span data-stu-id="6f6c5-215">Hyperlinks</span></span>

- <span data-ttu-id="6f6c5-216">避免使用裸 URL。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-216">Avoid using bare URLs.</span></span> <span data-ttu-id="6f6c5-217">链接应使用 Markdown 语法 `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="6f6c5-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="6f6c5-218">必要时可以使用裸 URL，但应使用反引号引起来。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="6f6c5-219">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="6f6c5-220">URL 链接应尽可能使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="6f6c5-221">链接必须具有友好名称，通常是链接主题的标题</span><span class="sxs-lookup"><span data-stu-id="6f6c5-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="6f6c5-222">底部“相关链接”部分中的所有项都应具有超链接。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="6f6c5-223">不要在超链接的括号内使用反引号、粗体或其他标记。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="6f6c5-224">链接到其他内容</span><span class="sxs-lookup"><span data-stu-id="6f6c5-224">Linking to other content</span></span>

<span data-ttu-id="6f6c5-225">发布系统支持两种类型的超链接：URL 和文件链接。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="6f6c5-226">URL 链接可以是相对于 docs.microsoft.com 根的 URL 路径。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="6f6c5-227">也可以是包含完整 URL 语法的绝对 URL。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="6f6c5-228">（例如：`https:/github.com/MicrosoftDocs/PowerShell-Docs`）</span><span class="sxs-lookup"><span data-stu-id="6f6c5-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="6f6c5-229">链接到 PowerShell-Docs 之外的内容时，或在 PowerShell-docs 内的 cmdlet 参考与概念性文章之间链接时，请使用 URL 链接。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="6f6c5-230">链接创建相对链接的最简单方法是从浏览器复制 URL，然后从粘贴到 Markdown 的值中删除 `https://docs.microsoft.com/en-us`。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-230">The simplest way to link create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="6f6c5-231">不要在 Microsoft 属性的 URL 中包含区域设置（例如，</span><span class="sxs-lookup"><span data-stu-id="6f6c5-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="6f6c5-232">请从 URL 中删除“/en-us”）。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="6f6c5-233">指向外部网站的所有 URL 都应使用 HTTPS（除非对目标站点无效）。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="6f6c5-234">从一个参考文章链接到另一个参考文章，或从一个概念性文章链接到另一个概念性文章时，使用文件链接。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="6f6c5-235">如果需要链接到特定版本的 PowerShell 的参考文章，则需要使用 URL 链接。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="6f6c5-236">文件链接包含相对文件路径（例如：`../folder/file.md`）</span><span class="sxs-lookup"><span data-stu-id="6f6c5-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="6f6c5-237">所有文件路径都使用正斜杠 (`/`) 字符</span><span class="sxs-lookup"><span data-stu-id="6f6c5-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="6f6c5-238">设置代码示例格式</span><span class="sxs-lookup"><span data-stu-id="6f6c5-238">Formatting code samples</span></span>

<span data-ttu-id="6f6c5-239">Markdown 支持两种不同的代码样式：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="6f6c5-240">代码范围（内联）- 用单个反引号 (`` ` ``) 字符标记。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="6f6c5-241">在段落中使用，而不是作为独立的块使用。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="6f6c5-242">代码块 - 使用三个反引号 (`` ``` ``) 字符串引起来的多行代码块。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="6f6c5-243">代码块的反引号后面还可能跟有一个语言标签。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="6f6c5-244">语言标签使代码块内容的语法突出显示。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="6f6c5-245">使用代码块</span><span class="sxs-lookup"><span data-stu-id="6f6c5-245">Using code blocks</span></span>

<span data-ttu-id="6f6c5-246">Markdown 允许以缩进方式表示代码块，但这种模式可能会出现问题，应避免使用此模式。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="6f6c5-247">所有代码块都应包含在代码隔离区中。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="6f6c5-248">代码隔离区是由三个反引号 (`` ``` ``) 字符串引起来的代码块。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="6f6c5-249">代码隔离区标记必须位于代码示例前后其自己的行上。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="6f6c5-250">代码块开头的标记可能具有可选的语言标签。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="6f6c5-251">Microsoft 的开放发布系统 (OPS) 使用语言标签来支持语法突出显示功能。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="6f6c5-252">OPS 还添加了可将代码块的内容复制到剪贴板的“复制”按钮  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="6f6c5-253">这样，你就可以将代码快速粘贴到脚本中，以测试代码示例。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="6f6c5-254">但是，并非文档中的所有示例都应该以这种方式运行。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="6f6c5-255">一些代码块是 PowerShell 概念的简单说明。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="6f6c5-256">文档中使用两种类型的代码块：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="6f6c5-257">说明性示例</span><span class="sxs-lookup"><span data-stu-id="6f6c5-257">Illustrative examples</span></span>
2. <span data-ttu-id="6f6c5-258">可执行示例</span><span class="sxs-lookup"><span data-stu-id="6f6c5-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="6f6c5-259">语法代码块</span><span class="sxs-lookup"><span data-stu-id="6f6c5-259">Syntax code blocks</span></span>

<span data-ttu-id="6f6c5-260">此示例演示 `Get-Command` cmdlet 所有可能的参数。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="6f6c5-261">此示例以通用术语描述 `for` 语句：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="6f6c5-262">说明性示例</span><span class="sxs-lookup"><span data-stu-id="6f6c5-262">Illustrative examples</span></span>

<span data-ttu-id="6f6c5-263">说明性示例用于解释 PowerShell 概念。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="6f6c5-264">不应将它们复制到剪贴板来执行。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="6f6c5-265">这些示例最常用于易于键入的简单示例。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="6f6c5-266">它们还用于演示命令语法的语法示例。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="6f6c5-267">代码块可能包含所演示命令的示例输出。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="6f6c5-268">以下简单示例演示 PowerShell 比较运算符：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="6f6c5-269">请注意，此示例提供简化的 PowerShell 提示，并显示生成的输出。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="6f6c5-270">在这种情况下，我们不希望读者复制并运行此示例。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="6f6c5-271">可执行示例</span><span class="sxs-lookup"><span data-stu-id="6f6c5-271">Executable examples</span></span>

<span data-ttu-id="6f6c5-272">更复杂的示例或应该便于复制和执行的示例应使用以下块样式标记：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="6f6c5-273">PowerShell 命令显示的输出应包含在 Output 代码块中，以防止语法突出显示  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="6f6c5-274">例如：</span><span class="sxs-lookup"><span data-stu-id="6f6c5-274">For example:</span></span>

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

<span data-ttu-id="6f6c5-275">Output 代码标签不是语法突出显示系统支持的一种正式“语言”  。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="6f6c5-276">但是，此标签非常有用，因为 OPS 会将“Output”标签添加到网页上的代码框框架中。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="6f6c5-277">“Output”代码框不会突出显示语法。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="6f6c5-278">编码样式规则</span><span class="sxs-lookup"><span data-stu-id="6f6c5-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="6f6c5-279">避免在代码示例中出现续行符</span><span class="sxs-lookup"><span data-stu-id="6f6c5-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="6f6c5-280">避免在 PowerShell 代码示例中使用续行符 (`` ` ``)。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="6f6c5-281">如果行尾出现多余的空格，会很难看到续行符，并且可能会引发问题。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="6f6c5-282">使用 PowerShell 展开来缩短包含大量参数的 cmdlet 的行长度。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="6f6c5-283">利用 PowerShell 的自然换行机会，如竖线 (`|`) 字符、左大括号、圆括号和方括号之后。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="6f6c5-284">避免在示例中使用 PowerShell 提示</span><span class="sxs-lookup"><span data-stu-id="6f6c5-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="6f6c5-285">不建议使用提示字符串，应该将其限制在旨在说明命令行用法的方案。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="6f6c5-286">对于其中大多数示例，提示字符串应为 `PS>`。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="6f6c5-287">此提示与特定于 OS 的指示器无关。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="6f6c5-288">如果示例演示改变提示的命令，或显示的路径对所演示的方案非常重要时，则需要提示。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="6f6c5-289">下面的示例演示使用注册表提供程序时提示的变化。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="6f6c5-290">请勿在示例中使用别名</span><span class="sxs-lookup"><span data-stu-id="6f6c5-290">Do not use aliases in examples</span></span>

<span data-ttu-id="6f6c5-291">应始终使用所有 cmdlet 和参数的全名，除非专门讨论别名。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="6f6c5-292">Cmdlet 和参数名称必须使用代码中定义的正确拼写。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="6f6c5-293">在示例中使用参数</span><span class="sxs-lookup"><span data-stu-id="6f6c5-293">Using parameters in examples</span></span>

<span data-ttu-id="6f6c5-294">避免使用位置参数。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-294">Avoid using positional parameters.</span></span> <span data-ttu-id="6f6c5-295">通常，即使是位置参数，也应始终在示例中包含参数名称。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-295">In general, you should use always include the parameter name in an example, even if the parameter positional.</span></span> <span data-ttu-id="6f6c5-296">这样可以减少在示例中产生混淆的可能性。</span><span class="sxs-lookup"><span data-stu-id="6f6c5-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6f6c5-297">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6f6c5-297">Next steps</span></span>

[<span data-ttu-id="6f6c5-298">编辑 cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="6f6c5-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
