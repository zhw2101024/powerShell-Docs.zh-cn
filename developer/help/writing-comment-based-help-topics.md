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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857573"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="2a92b-102">编写基于注释的帮助主题</span><span class="sxs-lookup"><span data-stu-id="2a92b-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="2a92b-103">可以使用特殊帮助注释关键字来编写基于注释的函数和脚本的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2a92b-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="2a92b-104">`Get-Help` Cmdlet 显示相同的格式，它将在其中显示从 XML 文件生成该 cmdlet 帮助主题中的基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="2a92b-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="2a92b-105">用户可以使用所有的参数`Get-Help`，如详细、 完整，示例中和联机，以显示函数和脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="2a92b-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="2a92b-106">你还可以编写脚本和函数的基于 XML 的帮助主题和帮助注释关键字用于将用户重定向到基于 XML 的主题或其他主题。</span><span class="sxs-lookup"><span data-stu-id="2a92b-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2a92b-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="2a92b-107">In This Section</span></span>

 <span data-ttu-id="2a92b-108">[基于注释的帮助的语法](./syntax-of-comment-based-help.md)介绍基于注释的帮助的语法。</span><span class="sxs-lookup"><span data-stu-id="2a92b-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="2a92b-109">[基于注释的帮助关键字](./comment-based-help-keywords.md)列出基于注释的帮助中的关键字。</span><span class="sxs-lookup"><span data-stu-id="2a92b-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="2a92b-110">[在 Functions 中放置基于注释的帮助](./placing-comment-based-help-in-functions.md)显示有关某个函数基于注释的帮助的放置位置。</span><span class="sxs-lookup"><span data-stu-id="2a92b-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="2a92b-111">[在脚本中放置基于注释的帮助](./placing-comment-based-help-in-scripts.md)显示放置位置的脚本基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="2a92b-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>