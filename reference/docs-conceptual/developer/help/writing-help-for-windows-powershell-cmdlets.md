---
title: 编写 PowerShell Cmdlet 的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361066"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="23aa8-102">编写 PowerShell Cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="23aa8-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="23aa8-103">PowerShell cmdlet 非常有用，但除非帮助主题清楚地说明了 cmdlet 的作用以及使用方式，否则 cmdlet 可能不会被使用，甚至更糟糕的是，它可能会使用户不快。</span><span class="sxs-lookup"><span data-stu-id="23aa8-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="23aa8-104">基于 XML 的 cmdlet 帮助文件格式增强了一致性，但有很大的帮助需要进一步的帮助。</span><span class="sxs-lookup"><span data-stu-id="23aa8-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="23aa8-105">如果你从未编写过 cmdlet 帮助，请查看以下准则。</span><span class="sxs-lookup"><span data-stu-id="23aa8-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="23aa8-106">以下部分介绍了创作 cmdlet 帮助主题所需的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="23aa8-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="23aa8-107">首先[创建 Cmdlet 帮助文件](./how-to-create-the-cmdlet-help-file.md)。</span><span class="sxs-lookup"><span data-stu-id="23aa8-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="23aa8-108">该主题包括顶级 XML 节点的说明。</span><span class="sxs-lookup"><span data-stu-id="23aa8-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="23aa8-109">编写 Cmdlet 帮助指南</span><span class="sxs-lookup"><span data-stu-id="23aa8-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="23aa8-110">编写良好</span><span class="sxs-lookup"><span data-stu-id="23aa8-110">Write well</span></span>
<span data-ttu-id="23aa8-111">任何内容都不会替代编写良好的主题。</span><span class="sxs-lookup"><span data-stu-id="23aa8-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="23aa8-112">如果您不是专业作者，请找到编写器或编辑器来帮助您。</span><span class="sxs-lookup"><span data-stu-id="23aa8-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="23aa8-113">另一种方法是将帮助文本复制到 Microsoft Word 中，并使用语法和拼写检查来改善您的工作。</span><span class="sxs-lookup"><span data-stu-id="23aa8-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="23aa8-114">简单编写</span><span class="sxs-lookup"><span data-stu-id="23aa8-114">Write simply</span></span>
<span data-ttu-id="23aa8-115">使用简单的单词和短语。</span><span class="sxs-lookup"><span data-stu-id="23aa8-115">Use simple words and phrases.</span></span>
<span data-ttu-id="23aa8-116">避免术语。</span><span class="sxs-lookup"><span data-stu-id="23aa8-116">Avoid jargon.</span></span>
<span data-ttu-id="23aa8-117">请注意，许多读者只配有外文字典和帮助主题。</span><span class="sxs-lookup"><span data-stu-id="23aa8-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="23aa8-118">一致性写入</span><span class="sxs-lookup"><span data-stu-id="23aa8-118">Write consistently</span></span>
<span data-ttu-id="23aa8-119">相关 cmdlet 的帮助应类似（例如，x-blade 和 set-x）。</span><span class="sxs-lookup"><span data-stu-id="23aa8-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="23aa8-120">为标准参数（如**Force**和**InputObject**）使用标准说明。</span><span class="sxs-lookup"><span data-stu-id="23aa8-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="23aa8-121">（从核心 cmdlet 的帮助中复制它们。）使用标准术语。</span><span class="sxs-lookup"><span data-stu-id="23aa8-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="23aa8-122">例如，使用 "参数" 而不是 "参数"，并使用 "cmdlet" 而不是 "命令" 或 "命令-let"。</span><span class="sxs-lookup"><span data-stu-id="23aa8-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="23aa8-123">使用谓词启动摘要</span><span class="sxs-lookup"><span data-stu-id="23aa8-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="23aa8-124">"摘要" 字段向用户通知 cmdlet 的功能，而不是它的作用或工作方式。</span><span class="sxs-lookup"><span data-stu-id="23aa8-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="23aa8-125">谓词创建一个基于任务的语句，该语句通知用户此 cmdlet 是否满足其要求。</span><span class="sxs-lookup"><span data-stu-id="23aa8-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="23aa8-126">使用简单的谓词，例如 "get"、"create" 和 "change"。</span><span class="sxs-lookup"><span data-stu-id="23aa8-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="23aa8-127">避免出现 "set"，这可能是个含糊的词，如 "修改"。</span><span class="sxs-lookup"><span data-stu-id="23aa8-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="23aa8-128">专注于对象</span><span class="sxs-lookup"><span data-stu-id="23aa8-128">Focus on objects</span></span>
<span data-ttu-id="23aa8-129">大多数 "get" cmdlet 显示某些内容，但其主要功能是获取对象。</span><span class="sxs-lookup"><span data-stu-id="23aa8-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="23aa8-130">在您的帮助中，将重点放在对象上，以便用户理解默认显示为多个，并可使用以不同方式为其检索的对象的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="23aa8-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="23aa8-131">编写详细说明</span><span class="sxs-lookup"><span data-stu-id="23aa8-131">Write detailed descriptions</span></span>
<span data-ttu-id="23aa8-132">简要列出 cmdlet 可在详细说明中执行的所有操作。</span><span class="sxs-lookup"><span data-stu-id="23aa8-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="23aa8-133">如果主函数是更改一个属性，但该 cmdlet 可以更改所有属性，请在详细说明中列出此项。</span><span class="sxs-lookup"><span data-stu-id="23aa8-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="23aa8-134">使用传统语法</span><span class="sxs-lookup"><span data-stu-id="23aa8-134">Use conventional syntax</span></span>
<span data-ttu-id="23aa8-135">使用适用于 Windows 和 UNIX 命令行帮助的标准巴科斯-诺尔范式格式。</span><span class="sxs-lookup"><span data-stu-id="23aa8-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="23aa8-136">使用 Microsoft .NET 框架类型作为参数值</span><span class="sxs-lookup"><span data-stu-id="23aa8-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="23aa8-137">参数值的占位符（在语法和参数说明中）显示参数将接受的对象的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="23aa8-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="23aa8-138">PowerShell 团队开发了此约定，以帮助用户了解 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="23aa8-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="23aa8-139">编写完整的参数说明</span><span class="sxs-lookup"><span data-stu-id="23aa8-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="23aa8-140">参数说明必须为用户通知两项内容：参数的作用（其效果）以及必须为参数值键入的内容。</span><span class="sxs-lookup"><span data-stu-id="23aa8-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="23aa8-141">编写实际示例</span><span class="sxs-lookup"><span data-stu-id="23aa8-141">Write practical examples</span></span>
<span data-ttu-id="23aa8-142">这些示例应说明如何使用所有参数，但最重要的一点是说明如何在实际任务中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="23aa8-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="23aa8-143">从一个简单的示例开始，编写越来越复杂的示例。</span><span class="sxs-lookup"><span data-stu-id="23aa8-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="23aa8-144">在最后的示例中，说明如何在管道中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="23aa8-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="23aa8-145">使用 "注释" 字段</span><span class="sxs-lookup"><span data-stu-id="23aa8-145">Use the Notes field</span></span>
<span data-ttu-id="23aa8-146">使用 "注释" 字段来解释用户需要了解 cmdlet 的概念。</span><span class="sxs-lookup"><span data-stu-id="23aa8-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="23aa8-147">你还可以使用注释来帮助用户避免常见错误。</span><span class="sxs-lookup"><span data-stu-id="23aa8-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="23aa8-148">避免更改 Url。</span><span class="sxs-lookup"><span data-stu-id="23aa8-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="23aa8-149">相反，请提供用户搜索搜索条件。</span><span class="sxs-lookup"><span data-stu-id="23aa8-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="23aa8-150">测试您的帮助</span><span class="sxs-lookup"><span data-stu-id="23aa8-150">Test your Help</span></span>
<span data-ttu-id="23aa8-151">测试帮助，就像测试代码一样。</span><span class="sxs-lookup"><span data-stu-id="23aa8-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="23aa8-152">让朋友和同事阅读你的帮助内容并提供反馈。</span><span class="sxs-lookup"><span data-stu-id="23aa8-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="23aa8-153">你还可以从新闻组请求反馈。</span><span class="sxs-lookup"><span data-stu-id="23aa8-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="23aa8-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23aa8-154">See Also</span></span>

 [<span data-ttu-id="23aa8-155">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="23aa8-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="23aa8-156">如何将 Cmdlet 名称和摘要添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-157">如何将详细描述添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="23aa8-158">如何将语法添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-159">如何将参数添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="23aa8-160">如何将输入类型添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-161">如何将返回值添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-162">如何向 Cmdlet 帮助主题添加注释</span><span class="sxs-lookup"><span data-stu-id="23aa8-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-163">如何将示例添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-164">如何将相关链接添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="23aa8-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="23aa8-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="23aa8-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)