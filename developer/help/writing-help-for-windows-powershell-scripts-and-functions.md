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
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083104"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="b662d-102">编写 PowerShell 脚本和函数的帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="b662d-103">PowerShell 脚本和函数应完整记录时与其他人共享。</span><span class="sxs-lookup"><span data-stu-id="b662d-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="b662d-104">`Get-Help` Cmdlet 显示脚本和函数的帮助主题中的相同的格式显示有关 cmdlet 和的所有帮助的方式`Get-Help`参数对脚本和函数的帮助主题的工作。</span><span class="sxs-lookup"><span data-stu-id="b662d-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="b662d-105">PowerShell 脚本可以在脚本中包括有关脚本的帮助主题以及有关每个函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span>
<span data-ttu-id="b662d-106">独立于脚本共享的函数可以包含其自己的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="b662d-107">本文档介绍了格式和正确放置的帮助主题，并建议内容的指导原则。</span><span class="sxs-lookup"><span data-stu-id="b662d-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="b662d-108">类型的脚本和函数帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="b662d-109">基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-109">Comment-Based Help</span></span>
<span data-ttu-id="b662d-110">介绍脚本或函数的帮助主题可以实现为一系列脚本或函数内的注释。</span><span class="sxs-lookup"><span data-stu-id="b662d-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span>
<span data-ttu-id="b662d-111">当在脚本中编写的脚本和函数基于注释的帮助，请注意规则放置基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="b662d-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span>
<span data-ttu-id="b662d-112">放置将确定是否`Get-Help`cmdlet 将脚本或函数与相关联的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span>
<span data-ttu-id="b662d-113">有关编写基于注释的帮助主题的详细信息，请参阅[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="b662d-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="b662d-114">基于 XML 的命令的帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-114">XML-Based Command Help</span></span>
<span data-ttu-id="b662d-115">可以在使用命令帮助架构的 XML 文件中实现介绍脚本或函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span>
<span data-ttu-id="b662d-116">若要将脚本或函数相关联的 XML 文件，请使用`ExternalHelp`注释关键字后面的路径和 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b662d-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="b662d-117">当`ExternalHelp`注释关键字是否存在，它将优先于基于注释的帮助，即使`Get-Help`找不到匹配的值的帮助文件`ExternalHelp`关键字。</span><span class="sxs-lookup"><span data-stu-id="b662d-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="b662d-118">联机帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-118">Online Help</span></span>
<span data-ttu-id="b662d-119">可以在 Internet 上发布您的帮助主题，然后将`Get-Help`打开主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-119">You can post your help topics on the Internet and then direct `Get-Help` to open the topics.</span></span>
<span data-ttu-id="b662d-120">有关编写基于注释的帮助主题的详细信息，请参阅[支持联机帮助](../module/supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="b662d-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="b662d-121">没有已建立的方法以进行写入 （"关于"） 的脚本和函数的主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="b662d-122">但是，您可以发布 Internet 列表上的概念性主题的主题，因此其 Url 命令的帮助主题的相关链接部分中。</span><span class="sxs-lookup"><span data-stu-id="b662d-122">However, you can post conceptual topics on the Internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="b662d-123">脚本和函数的内容注意事项帮助</span><span class="sxs-lookup"><span data-stu-id="b662d-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="b662d-124">如果你正在使用只有几个可用命令的帮助部分编写非常简短的帮助主题，请务必包括脚本或函数参数的详细描述。</span><span class="sxs-lookup"><span data-stu-id="b662d-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="b662d-125">此外在示例部分中，包含一个或两个示例命令即使你决定以忽略此参数的示例说明。</span><span class="sxs-lookup"><span data-stu-id="b662d-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="b662d-126">在所有的说明，请参阅命令的访问权限的脚本或函数。</span><span class="sxs-lookup"><span data-stu-id="b662d-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="b662d-127">此信息可帮助用户了解和管理命令。</span><span class="sxs-lookup"><span data-stu-id="b662d-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="b662d-128">例如，以下详细的说明指出新建主题命令是一个脚本。</span><span class="sxs-lookup"><span data-stu-id="b662d-128">For example, the following detailed description states that the New-Topic command is a script.</span></span> <span data-ttu-id="b662d-129">这将提醒用户他们需要在运行时指定的路径和完整名称。</span><span class="sxs-lookup"><span data-stu-id="b662d-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="b662d-130">"新建主题脚本...在输入文件中创建空白的概念主题，为每个主题名称"</span><span class="sxs-lookup"><span data-stu-id="b662d-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="b662d-131">下面详细的说明指出`Disable-PSRemoting`是一个函数。</span><span class="sxs-lookup"><span data-stu-id="b662d-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="b662d-132">此信息在会话中包括多个命令具有相同的名称，其中一些可能被隐藏某一命令优先级更高时向用户特别有用。</span><span class="sxs-lookup"><span data-stu-id="b662d-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="b662d-133">`Disable-PSRemoting`函数可禁用本地计算机上的所有会话配置...</span><span class="sxs-lookup"><span data-stu-id="b662d-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="b662d-134">在脚本的帮助主题中，介绍如何使用此脚本作为一个整体。</span><span class="sxs-lookup"><span data-stu-id="b662d-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="b662d-135">如果您还会在脚本中编写函数的帮助主题，提到您脚本的帮助主题中的函数和脚本帮助主题的相关链接部分中包括对函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span> <span data-ttu-id="b662d-136">相反，如果函数是脚本的一部分，阐释函数帮助主题中该函数在脚本和它可以如何使用独立中所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="b662d-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="b662d-137">然后列出函数帮助主题的相关链接部分中的脚本帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="b662d-138">在编写脚本的帮助主题的示例，请务必在示例命令中包含的脚本文件的路径。</span><span class="sxs-lookup"><span data-stu-id="b662d-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="b662d-139">这将提醒用户他们都必须显式指定的路径，即使脚本位于当前目录。</span><span class="sxs-lookup"><span data-stu-id="b662d-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="b662d-140">在函数的帮助主题中，提醒用户，仅在当前会话中存在的函数，若要在其他会话中使用它，他们需要添加它，或将其添加 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="b662d-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="b662d-141">`Get-Help` 仅当在正确的位置保存的脚本文件和帮助主题文件时将显示有关脚本或函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b662d-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="b662d-142">因此，不需要包含有关安装 PowerShell，或保存或安装脚本或函数的帮助主题中的脚本或函数的说明。</span><span class="sxs-lookup"><span data-stu-id="b662d-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="b662d-143">相反，包括用于分发的脚本或函数的文档中的任何安装说明。</span><span class="sxs-lookup"><span data-stu-id="b662d-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="b662d-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b662d-144">See Also</span></span>

 [<span data-ttu-id="b662d-145">编写脚本和函数的基于 XML 的帮助主题</span><span class="sxs-lookup"><span data-stu-id="b662d-145">Writing XML-Based Help Topics for Scripts and Functions</span></span>](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [<span data-ttu-id="b662d-146">命令为编写基于 XML 的帮助主题</span><span class="sxs-lookup"><span data-stu-id="b662d-146">Writing XML-Based Help Topics for Commands</span></span>](./writing-xml-based-help-topics-for-commands.md)

 [<span data-ttu-id="b662d-147">编写基于注释的帮助主题</span><span class="sxs-lookup"><span data-stu-id="b662d-147">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
