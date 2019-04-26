---
title: PowerShell cmdlet 编写帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083155"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="2128c-102">PowerShell Cmdlet 编写帮助</span><span class="sxs-lookup"><span data-stu-id="2128c-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="2128c-103">PowerShell cmdlet 可能很有用，但除非您的帮助主题清楚地说明该 cmdlet 的用途以及如何使用它，该 cmdlet 可能会开始使用或更糟糕的是，它可能会对用户。</span><span class="sxs-lookup"><span data-stu-id="2128c-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="2128c-104">基于 XML 的 cmdlet 帮助文件格式可提高一致性，但极佳的帮助要求更高。</span><span class="sxs-lookup"><span data-stu-id="2128c-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="2128c-105">如果您永远不会编写 cmdlet 帮助，请查看以下准则。</span><span class="sxs-lookup"><span data-stu-id="2128c-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="2128c-106">以下部分中描述所需编写 cmdlet 帮助主题的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="2128c-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="2128c-107">开头[创建 Cmdlet 帮助文件](./how-to-create-the-cmdlet-help-file.md)。</span><span class="sxs-lookup"><span data-stu-id="2128c-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="2128c-108">该主题包括的顶级 XML 节点的说明。</span><span class="sxs-lookup"><span data-stu-id="2128c-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="2128c-109">有关 Cmdlet 的帮助的作者指南</span><span class="sxs-lookup"><span data-stu-id="2128c-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="2128c-110">编写</span><span class="sxs-lookup"><span data-stu-id="2128c-110">Write well</span></span>
<span data-ttu-id="2128c-111">执行任何操作将替换编写良好的主题。</span><span class="sxs-lookup"><span data-stu-id="2128c-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="2128c-112">如果您不是专业的编写器，找到要帮助您的编写器或编辑器。</span><span class="sxs-lookup"><span data-stu-id="2128c-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="2128c-113">另一种方法是将帮助文本复制到 Microsoft Word 和使用语法和拼写检查改进您的工作。</span><span class="sxs-lookup"><span data-stu-id="2128c-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="2128c-114">只需编写</span><span class="sxs-lookup"><span data-stu-id="2128c-114">Write simply</span></span>
<span data-ttu-id="2128c-115">使用简单的词和短语。</span><span class="sxs-lookup"><span data-stu-id="2128c-115">Use simple words and phrases.</span></span>
<span data-ttu-id="2128c-116">避免术语。</span><span class="sxs-lookup"><span data-stu-id="2128c-116">Avoid jargon.</span></span>
<span data-ttu-id="2128c-117">请考虑许多读者都配备仅有外语言字典和帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2128c-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="2128c-118">一致地编写</span><span class="sxs-lookup"><span data-stu-id="2128c-118">Write consistently</span></span>
<span data-ttu-id="2128c-119">有关相关的 cmdlet 应类似 （如 get-x 和集 x） 帮助。</span><span class="sxs-lookup"><span data-stu-id="2128c-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="2128c-120">使用标准说明对于标准参数，如**Force**并**InputObject**。</span><span class="sxs-lookup"><span data-stu-id="2128c-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="2128c-121">（将它们复制的帮助中的核心 cmdlet。）使用标准条款。</span><span class="sxs-lookup"><span data-stu-id="2128c-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="2128c-122">例如，使用"参数"、 不"参数"和使用"cmdlet"不"命令"或者"command-let 命令。"</span><span class="sxs-lookup"><span data-stu-id="2128c-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="2128c-123">以动词开头摘要</span><span class="sxs-lookup"><span data-stu-id="2128c-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="2128c-124">摘要字段将通知用户哪些 cmdlet 不会它是什么或其工作原理。</span><span class="sxs-lookup"><span data-stu-id="2128c-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="2128c-125">谓词创建一个基于任务的语句，通知用户，此 cmdlet 满足其要求。</span><span class="sxs-lookup"><span data-stu-id="2128c-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="2128c-126">使用简单动词，如"get"、"创建"和"更改"。</span><span class="sxs-lookup"><span data-stu-id="2128c-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="2128c-127">避免"set"，可以是模糊和"修改"等花哨的单词。</span><span class="sxs-lookup"><span data-stu-id="2128c-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="2128c-128">专注于对象</span><span class="sxs-lookup"><span data-stu-id="2128c-128">Focus on objects</span></span>
<span data-ttu-id="2128c-129">大多数"get"cmdlet 显示某些内容，但其主要功能是用于获取的对象。</span><span class="sxs-lookup"><span data-stu-id="2128c-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="2128c-130">在您的帮助，重点介绍该对象，以便用户了解的默认显示的许多，其中一个，并且它们可以使用的方法和属性不同的方式为其检索到的对象。</span><span class="sxs-lookup"><span data-stu-id="2128c-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="2128c-131">写入详细的说明</span><span class="sxs-lookup"><span data-stu-id="2128c-131">Write detailed descriptions</span></span>
<span data-ttu-id="2128c-132">简要列出该 cmdlet 可以执行操作的详细说明中的所有内容。</span><span class="sxs-lookup"><span data-stu-id="2128c-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="2128c-133">如果主要功能是若要更改一个属性，但该 cmdlet 可以更改所有属性，列出该标签中详细说明。</span><span class="sxs-lookup"><span data-stu-id="2128c-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="2128c-134">使用传统语法</span><span class="sxs-lookup"><span data-stu-id="2128c-134">Use conventional syntax</span></span>
<span data-ttu-id="2128c-135">使用标准的巴科斯-诺尔格式将是很常见的 Windows 和 UNIX 命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="2128c-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="2128c-136">使用 Microsoft.NET Framework 类型的参数值</span><span class="sxs-lookup"><span data-stu-id="2128c-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="2128c-137">（在语法和参数的说明） 的参数值的占位符显示该参数将接受的对象的.NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="2128c-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="2128c-138">PowerShell 团队开发了此约定，可帮助指导有关.NET Framework 的用户。</span><span class="sxs-lookup"><span data-stu-id="2128c-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="2128c-139">写入完整的参数说明</span><span class="sxs-lookup"><span data-stu-id="2128c-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="2128c-140">参数说明必须让用户添加了两件事： 哪些参数的作用 （其会有影响），他们必须输入的参数值。</span><span class="sxs-lookup"><span data-stu-id="2128c-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="2128c-141">编写实际示例</span><span class="sxs-lookup"><span data-stu-id="2128c-141">Write practical examples</span></span>
<span data-ttu-id="2128c-142">这些示例应显示如何使用的所有参数，但最重要的事情是说明如何在实际的任务中使用该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2128c-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="2128c-143">启动一个简单的示例，并编写日益复杂的示例。</span><span class="sxs-lookup"><span data-stu-id="2128c-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="2128c-144">在最后一个示例，演示如何在管道中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2128c-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="2128c-145">使用说明字段</span><span class="sxs-lookup"><span data-stu-id="2128c-145">Use the Notes field</span></span>
<span data-ttu-id="2128c-146">说明字段用于解释用户需要了解该 cmdlet 的概念。</span><span class="sxs-lookup"><span data-stu-id="2128c-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="2128c-147">说明还可用于帮助用户避免常见错误。</span><span class="sxs-lookup"><span data-stu-id="2128c-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="2128c-148">避免 Url，因为它们会更改。</span><span class="sxs-lookup"><span data-stu-id="2128c-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="2128c-149">相反，提供要搜索的用户术语。</span><span class="sxs-lookup"><span data-stu-id="2128c-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="2128c-150">测试您的帮助</span><span class="sxs-lookup"><span data-stu-id="2128c-150">Test your Help</span></span>
<span data-ttu-id="2128c-151">测试帮助，就像测试你的代码。</span><span class="sxs-lookup"><span data-stu-id="2128c-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="2128c-152">朋友和同事读取您的帮助内容，并提供反馈。</span><span class="sxs-lookup"><span data-stu-id="2128c-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="2128c-153">此外可以要求来自新闻组的反馈。</span><span class="sxs-lookup"><span data-stu-id="2128c-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="2128c-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2128c-154">See Also</span></span>

 [<span data-ttu-id="2128c-155">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="2128c-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="2128c-156">如何将 Cmdlet 名称和摘要添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-157">如何将详细的说明添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="2128c-158">如何将语法添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-159">如何将参数添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="2128c-160">如何添加到 Cmdlet 帮助主题的输入类型</span><span class="sxs-lookup"><span data-stu-id="2128c-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-161">如何将返回值添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-162">如何添加说明 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-163">如何添加到 Cmdlet 帮助主题的示例</span><span class="sxs-lookup"><span data-stu-id="2128c-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-164">如何将相关的链接添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="2128c-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="2128c-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2128c-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)