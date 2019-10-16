---
title: 编写基于注释的帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e619ab16-90ad-46e9-9bde-d6dce492ba56
caps.latest.revision: 4
ms.openlocfilehash: e3d32f36b597088abc41e229bb0955c1b25504e6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361076"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="73e49-102">编写基于注释的帮助主题</span><span class="sxs-lookup"><span data-stu-id="73e49-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="73e49-103">您可以使用特殊的帮助注释关键字为函数和脚本编写基于注释的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="73e49-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="73e49-104">@No__t cmdlet 显示基于注释的帮助，其格式与用于显示 XML 文件中生成的 cmdlet 帮助主题的格式相同。</span><span class="sxs-lookup"><span data-stu-id="73e49-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="73e49-105">用户可以使用 `Get-Help` 的所有参数，如详细、完整、示例和联机，以显示函数和脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="73e49-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="73e49-106">你还可以为脚本和函数编写基于 XML 的帮助主题，并使用帮助注释关键字将用户重定向到基于 XML 的主题或其他主题。</span><span class="sxs-lookup"><span data-stu-id="73e49-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="73e49-107">本部分内容</span><span class="sxs-lookup"><span data-stu-id="73e49-107">In This Section</span></span>

 <span data-ttu-id="73e49-108">[基于注释的帮助的语法](./syntax-of-comment-based-help.md)介绍基于注释的帮助的语法。</span><span class="sxs-lookup"><span data-stu-id="73e49-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="73e49-109">[基于注释的帮助关键字](./comment-based-help-keywords.md)在基于注释的帮助中列出关键字。</span><span class="sxs-lookup"><span data-stu-id="73e49-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="73e49-110">[在函数中放置基于注释的帮助](./placing-comment-based-help-in-functions.md)显示为函数设置基于注释的帮助的位置。</span><span class="sxs-lookup"><span data-stu-id="73e49-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="73e49-111">[在脚本中放置基于注释的帮助](./placing-comment-based-help-in-scripts.md)显示在何处放置脚本的基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="73e49-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>