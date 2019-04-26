---
title: 如何添加到 Cmdlet 帮助主题的示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083461"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="19b5f-102">如何向 Cmdlet 帮助主题添加示例</span><span class="sxs-lookup"><span data-stu-id="19b5f-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="19b5f-103">须知中的 Cmdlet 帮助示例</span><span class="sxs-lookup"><span data-stu-id="19b5f-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="19b5f-104">帮助显示示例的视图</span><span class="sxs-lookup"><span data-stu-id="19b5f-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="19b5f-105">添加示例节点</span><span class="sxs-lookup"><span data-stu-id="19b5f-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="19b5f-106">添加上述字符</span><span class="sxs-lookup"><span data-stu-id="19b5f-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="19b5f-107">添加命令</span><span class="sxs-lookup"><span data-stu-id="19b5f-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="19b5f-108">添加说明</span><span class="sxs-lookup"><span data-stu-id="19b5f-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="19b5f-109">添加示例输出</span><span class="sxs-lookup"><span data-stu-id="19b5f-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="19b5f-110">须知中的 Cmdlet 帮助示例</span><span class="sxs-lookup"><span data-stu-id="19b5f-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="19b5f-111">列出了所有参数名称在命令中，即使是可选的参数名称。</span><span class="sxs-lookup"><span data-stu-id="19b5f-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="19b5f-112">这可帮助用户轻松地解释该命令。</span><span class="sxs-lookup"><span data-stu-id="19b5f-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="19b5f-113">避免别名和部分参数名称，即使它们在 Windows PowerShell® 中工作。</span><span class="sxs-lookup"><span data-stu-id="19b5f-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="19b5f-114">在示例说明中，介绍了合理的有关构造的命令。</span><span class="sxs-lookup"><span data-stu-id="19b5f-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="19b5f-115">说明了为什么选择特定参数和值，以及如何使用变量。</span><span class="sxs-lookup"><span data-stu-id="19b5f-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="19b5f-116">如果该命令使用表达式，其详细信息中进行说明。</span><span class="sxs-lookup"><span data-stu-id="19b5f-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="19b5f-117">如果该命令使用对象的属性和方法，尤其是在默认显示中，不会显示的属性将使用示例，因为有机会告诉用户有关的对象信息。</span><span class="sxs-lookup"><span data-stu-id="19b5f-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="19b5f-118">帮助显示示例的视图</span><span class="sxs-lookup"><span data-stu-id="19b5f-118">Help Views that Display Examples</span></span>

<span data-ttu-id="19b5f-119">仅 cmdlet 帮助的详细和完整视图中显示的示例。</span><span class="sxs-lookup"><span data-stu-id="19b5f-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="19b5f-120">添加示例节点</span><span class="sxs-lookup"><span data-stu-id="19b5f-120">Adding an Examples Node</span></span>

<span data-ttu-id="19b5f-121">下面的 XML 演示如何添加包含一个示例中节点的示例节点。</span><span class="sxs-lookup"><span data-stu-id="19b5f-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="19b5f-122">添加你想要在本主题中包含每个示例的示例中其他节点。</span><span class="sxs-lookup"><span data-stu-id="19b5f-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="19b5f-123">添加示例标题</span><span class="sxs-lookup"><span data-stu-id="19b5f-123">Adding an Example Title</span></span>

<span data-ttu-id="19b5f-124">下面的 XML 演示如何以添加该示例的标题。</span><span class="sxs-lookup"><span data-stu-id="19b5f-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="19b5f-125">标题用于设置除其他示例的示例。</span><span class="sxs-lookup"><span data-stu-id="19b5f-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="19b5f-126">Windows PowerShell® 使用标准标头包含顺序示例号。</span><span class="sxs-lookup"><span data-stu-id="19b5f-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="19b5f-127">添加上述字符</span><span class="sxs-lookup"><span data-stu-id="19b5f-127">Adding Preceding Characters</span></span>

<span data-ttu-id="19b5f-128">下面的 XML 演示如何添加 （不带任何干预空格） 的示例命令前立即显示的字符，如 Windows PowerShell 提示符下。</span><span class="sxs-lookup"><span data-stu-id="19b5f-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="19b5f-129">Windows PowerShell® 使用 Windows PowerShell 提示符：C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="19b5f-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="19b5f-130">添加命令</span><span class="sxs-lookup"><span data-stu-id="19b5f-130">Adding the Command</span></span>

<span data-ttu-id="19b5f-131">下面的 XML 演示如何以添加该示例的实际命令。</span><span class="sxs-lookup"><span data-stu-id="19b5f-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="19b5f-132">在添加该命令时，键入整个名称 （不使用别名） 的 cmdlet 和参数。</span><span class="sxs-lookup"><span data-stu-id="19b5f-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="19b5f-133">此外，使用小写字母，只要有可能。</span><span class="sxs-lookup"><span data-stu-id="19b5f-133">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="19b5f-134">添加说明</span><span class="sxs-lookup"><span data-stu-id="19b5f-134">Adding a Description</span></span>

<span data-ttu-id="19b5f-135">下面的 XML 演示如何添加该示例的说明。</span><span class="sxs-lookup"><span data-stu-id="19b5f-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="19b5f-136">Windows PowerShell® 使用一组\<maml:para > 标记的描述，即使多个\<maml:para >，可以使用标记。</span><span class="sxs-lookup"><span data-stu-id="19b5f-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="19b5f-137">添加示例输出</span><span class="sxs-lookup"><span data-stu-id="19b5f-137">Adding Example Output</span></span>

<span data-ttu-id="19b5f-138">下面的 XML 演示如何添加命令的输出。</span><span class="sxs-lookup"><span data-stu-id="19b5f-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="19b5f-139">命令的结果信息是可选的但在某些情况下很有帮助，以演示中使用特定参数的效果。</span><span class="sxs-lookup"><span data-stu-id="19b5f-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="19b5f-140">Windows PowerShell® 使用两个集为空\<maml:para > 标记与命令分离命令输出。</span><span class="sxs-lookup"><span data-stu-id="19b5f-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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