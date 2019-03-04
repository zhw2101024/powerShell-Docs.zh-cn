---
title: 语法基于注释的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855543"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="e7792-102">基于注释的帮助的语法</span><span class="sxs-lookup"><span data-stu-id="e7792-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="e7792-103">本部分介绍基于注释的帮助的语法。</span><span class="sxs-lookup"><span data-stu-id="e7792-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="e7792-104">语法关系图</span><span class="sxs-lookup"><span data-stu-id="e7792-104">Syntax Diagram</span></span>

 <span data-ttu-id="e7792-105">基于注释的帮助的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e7792-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="e7792-106">语法说明</span><span class="sxs-lookup"><span data-stu-id="e7792-106">Syntax Description</span></span>

 <span data-ttu-id="e7792-107">基于注释的帮助编写为一系列的注释。</span><span class="sxs-lookup"><span data-stu-id="e7792-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="e7792-108">您可以在每行注释之前, 键入注释符号 （#） 也可以使用"\<#"和"#>"符号创建注释块。</span><span class="sxs-lookup"><span data-stu-id="e7792-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="e7792-109">注释块中的所有行被都解释为注释。</span><span class="sxs-lookup"><span data-stu-id="e7792-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="e7792-110">由一个关键字定义的基于注释的帮助每个部分，每个关键字前面是句点 （.）。</span><span class="sxs-lookup"><span data-stu-id="e7792-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="e7792-111">关键字可以按任何顺序出现。</span><span class="sxs-lookup"><span data-stu-id="e7792-111">The keywords can appear in any order.</span></span> <span data-ttu-id="e7792-112">关键字名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e7792-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="e7792-113">注释块必须包含至少一个帮助关键字。</span><span class="sxs-lookup"><span data-stu-id="e7792-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="e7792-114">某些关键字，如示例中，可以在相同的注释块中出现多次。</span><span class="sxs-lookup"><span data-stu-id="e7792-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="e7792-115">为每个关键字的帮助内容的关键字后的行上开始，并可以跨多个行。</span><span class="sxs-lookup"><span data-stu-id="e7792-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="e7792-116">所有基于注释的帮助主题中的行必须是连续的。</span><span class="sxs-lookup"><span data-stu-id="e7792-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="e7792-117">如果基于注释的帮助主题后跟注释不是帮助的帮助主题的一部分，必须是帮助的最后一个非帮助注释行和基于注释的开头之间的至少一个空白行。</span><span class="sxs-lookup"><span data-stu-id="e7792-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="e7792-118">例如，包含以下基于注释的帮助主题。描述关键字和其值，该值是函数或脚本的说明。</span><span class="sxs-lookup"><span data-stu-id="e7792-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```