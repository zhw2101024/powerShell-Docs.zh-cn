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
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367716"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="7ea9c-102">编写 PowerShell 脚本和函数的帮助</span><span class="sxs-lookup"><span data-stu-id="7ea9c-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="7ea9c-103">当 PowerShell 脚本和函数与其他人共享时，它们应该是完整记录的。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="7ea9c-104">`Get-Help` cmdlet 显示脚本和函数帮助主题，其格式与显示 cmdlet 的帮助相同，并且所有 `Get-Help` 参数都适用于脚本和函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="7ea9c-105">PowerShell 脚本可以包括有关脚本的帮助主题，以及有关脚本中每个函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span>
<span data-ttu-id="7ea9c-106">独立于脚本共享的函数可以包含它们自己的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="7ea9c-107">本文档介绍了 "帮助" 主题的格式和正确位置，并为内容提供指导原则。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="7ea9c-108">脚本和函数帮助的类型</span><span class="sxs-lookup"><span data-stu-id="7ea9c-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="7ea9c-109">基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="7ea9c-109">Comment-Based Help</span></span>
<span data-ttu-id="7ea9c-110">描述脚本或函数的帮助主题可作为脚本或函数中的一组注释实现。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span>
<span data-ttu-id="7ea9c-111">为脚本编写基于注释的帮助和脚本中的函数时，请注意用于放置基于注释的帮助的规则。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span>
<span data-ttu-id="7ea9c-112">此位置确定 `Get-Help` cmdlet 是否将帮助主题与脚本或函数关联。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span>
<span data-ttu-id="7ea9c-113">有关编写基于注释的帮助主题的详细信息，请参阅[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="7ea9c-114">基于 XML 的命令帮助</span><span class="sxs-lookup"><span data-stu-id="7ea9c-114">XML-Based Command Help</span></span>
<span data-ttu-id="7ea9c-115">描述脚本或函数的帮助主题可以在使用 command help 架构的 XML 文件中实现。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span>
<span data-ttu-id="7ea9c-116">若要将脚本或函数与 XML 文件相关联，请使用 `ExternalHelp` comment 关键字，后跟 XML 文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="7ea9c-117">如果 `ExternalHelp` comment 关键字存在，则它将优先于基于注释的帮助，即使 `Get-Help` 找不到与 `ExternalHelp` 关键字的值匹配的帮助文件也是如此。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="7ea9c-118">联机帮助</span><span class="sxs-lookup"><span data-stu-id="7ea9c-118">Online Help</span></span>
<span data-ttu-id="7ea9c-119">你可以在 Internet 上发布帮助主题，然后直接 `Get-Help` 来打开这些主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-119">You can post your help topics on the Internet and then direct `Get-Help` to open the topics.</span></span>
<span data-ttu-id="7ea9c-120">有关编写基于注释的帮助主题的详细信息，请参阅[支持联机帮助](../module/supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="7ea9c-121">没有已建立的方法来编写脚本和函数的概念（"关于"）主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="7ea9c-122">但是，你可以在 "命令帮助" 主题的 "相关链接" 部分中，在 Internet 上列出主题及其 Url。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-122">However, you can post conceptual topics on the Internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="7ea9c-123">脚本和函数帮助的内容注意事项</span><span class="sxs-lookup"><span data-stu-id="7ea9c-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="7ea9c-124">如果你正在编写一个非常简短的帮助主题，其中只包含几个可用的命令帮助部分，请确保包含脚本或函数参数的明确说明。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="7ea9c-125">还在 "示例" 部分中包括一个或两个示例命令，即使您决定省略示例说明。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="7ea9c-126">在所有说明中，请将命令作为脚本或函数引用。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="7ea9c-127">此信息可帮助用户了解和管理命令。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="7ea9c-128">例如，下面的详细说明指出，新的主题命令是一个脚本。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-128">For example, the following detailed description states that the New-Topic command is a script.</span></span> <span data-ttu-id="7ea9c-129">这会提醒用户他们在运行时需要指定路径和全名。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="7ea9c-130">"新的主题脚本为输入文件中的每个主题名称创建一个空白的概念主题 ..."</span><span class="sxs-lookup"><span data-stu-id="7ea9c-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="7ea9c-131">以下详细说明表明 `Disable-PSRemoting` 是一个函数。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="7ea9c-132">当会话中包含多个具有相同名称的命令时，此信息对用户特别有用，其中有些命令可能由优先级较高的命令隐藏。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="7ea9c-133">`Disable-PSRemoting` 函数将禁用本地计算机上的所有会话配置 。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="7ea9c-134">在脚本帮助主题中，介绍如何将该脚本作为一个整体使用。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="7ea9c-135">如果你还在脚本中编写函数的帮助主题，请在脚本帮助主题的 "相关链接" 部分中提到函数帮助主题，并将其包含在脚本帮助主题中。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span> <span data-ttu-id="7ea9c-136">相反，当某个函数作为脚本的一部分时，将在函数帮助主题中介绍函数在脚本中所扮演的角色以及如何单独使用该函数。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="7ea9c-137">然后在函数帮助主题的 "相关链接" 部分中列出脚本帮助主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="7ea9c-138">编写脚本帮助主题的示例时，请确保在示例命令中包含脚本文件的路径。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="7ea9c-139">这会提醒用户他们必须显式指定路径，即使脚本在当前目录中也是如此。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="7ea9c-140">在函数帮助主题中，提醒用户此函数仅在当前会话中存在，若要在其他会话中使用它，需要添加它，或者将其添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="7ea9c-141">只有在将脚本文件和帮助主题文件保存到正确的位置时，`Get-Help` 才会显示脚本或函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="7ea9c-142">因此，在脚本或函数帮助主题中包含用于安装 PowerShell 或保存或安装脚本或函数的说明并不有用。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="7ea9c-143">相反，请在用于分发脚本或函数的文档中包含任何安装说明。</span><span class="sxs-lookup"><span data-stu-id="7ea9c-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ea9c-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ea9c-144">See Also</span></span>

[<span data-ttu-id="7ea9c-145">编写基于注释的帮助主题</span><span class="sxs-lookup"><span data-stu-id="7ea9c-145">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
