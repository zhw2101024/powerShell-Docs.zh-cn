---
title: 如何向 Cmdlet 帮助主题添加示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368106"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="4f6a7-102">如何向 Cmdlet 帮助主题添加示例</span><span class="sxs-lookup"><span data-stu-id="4f6a7-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="4f6a7-103">有关 Cmdlet 帮助中的示例的注意事项</span><span class="sxs-lookup"><span data-stu-id="4f6a7-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="4f6a7-104">列出命令中的所有参数名称，即使参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="4f6a7-105">这可帮助用户轻松解释命令。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="4f6a7-106">避免使用别名和部分参数名称，即使它们适用于 Windows PowerShell®。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="4f6a7-107">在示例说明中，说明了该命令的构造的有理数。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="4f6a7-108">说明选择特定参数和值的原因，以及如何使用变量。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="4f6a7-109">如果该命令使用表达式，请详细说明。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="4f6a7-110">如果该命令使用对象的属性和方法（特别是未出现在默认显示中的属性），则使用此示例作为机会向用户通知该对象。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="4f6a7-111">显示示例的帮助视图</span><span class="sxs-lookup"><span data-stu-id="4f6a7-111">Help Views that Display Examples</span></span>

<span data-ttu-id="4f6a7-112">示例仅出现在 cmdlet 帮助的详细视图和完整视图中。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="4f6a7-113">添加示例节点</span><span class="sxs-lookup"><span data-stu-id="4f6a7-113">Adding an Examples Node</span></span>

<span data-ttu-id="4f6a7-114">下面的 XML 演示如何添加一个示例节点，其中包含一个示例节点。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="4f6a7-115">为要包含在主题中的每个示例添加其他示例节点。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="4f6a7-116">添加示例标题</span><span class="sxs-lookup"><span data-stu-id="4f6a7-116">Adding an Example Title</span></span>

<span data-ttu-id="4f6a7-117">下面的 XML 演示如何添加示例的标题。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="4f6a7-118">标题用于设置除其他示例之外的示例。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="4f6a7-119">Windows PowerShell®使用包含连续示例编号的标准标头。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="4f6a7-120">添加前面的字符</span><span class="sxs-lookup"><span data-stu-id="4f6a7-120">Adding Preceding Characters</span></span>

<span data-ttu-id="4f6a7-121">下面的 XML 演示如何添加字符，如 Windows PowerShell prompt，它们紧靠在示例命令之前（无需任何插入空格）。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="4f6a7-122">Windows PowerShell®使用 Windows PowerShell 提示符： C:\PS >。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="4f6a7-123">添加命令</span><span class="sxs-lookup"><span data-stu-id="4f6a7-123">Adding the Command</span></span>

<span data-ttu-id="4f6a7-124">下面的 XML 演示如何添加示例的实际命令。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="4f6a7-125">添加命令时，请键入 cmdlet 和参数的完整名称（不使用别名）。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="4f6a7-126">同时，尽可能使用小写字符。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="4f6a7-127">添加说明</span><span class="sxs-lookup"><span data-stu-id="4f6a7-127">Adding a Description</span></span>

<span data-ttu-id="4f6a7-128">下面的 XML 演示如何添加示例的说明。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="4f6a7-129">Windows PowerShell®为说明使用一组 \<maml：段落 > 标记，即使可以使用多个 \<maml：段落 > 标记。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="4f6a7-130">添加示例输出</span><span class="sxs-lookup"><span data-stu-id="4f6a7-130">Adding Example Output</span></span>

<span data-ttu-id="4f6a7-131">下面的 XML 演示如何添加命令的输出。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="4f6a7-132">命令结果信息是可选的，但在某些情况下，演示使用特定参数的效果会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="4f6a7-133">Windows PowerShell®使用两组空白 \<maml：段落 > 标记将命令输出与命令分离。</span><span class="sxs-lookup"><span data-stu-id="4f6a7-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```