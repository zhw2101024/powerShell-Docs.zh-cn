---
title: 基于注释的帮助的语法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367756"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="f398a-102">基于注释的帮助的语法</span><span class="sxs-lookup"><span data-stu-id="f398a-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="f398a-103">本部分介绍基于注释的帮助的语法。</span><span class="sxs-lookup"><span data-stu-id="f398a-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="f398a-104">语法关系图</span><span class="sxs-lookup"><span data-stu-id="f398a-104">Syntax Diagram</span></span>

 <span data-ttu-id="f398a-105">基于注释的帮助的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="f398a-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="f398a-106">语法说明</span><span class="sxs-lookup"><span data-stu-id="f398a-106">Syntax Description</span></span>

 <span data-ttu-id="f398a-107">基于注释的帮助以一系列注释形式编写。</span><span class="sxs-lookup"><span data-stu-id="f398a-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="f398a-108">可以在每行注释之前键入注释符号（#），也可以使用 "\<#" 和 "# >" 符号创建注释块。</span><span class="sxs-lookup"><span data-stu-id="f398a-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="f398a-109">注释块内的所有行都解释为注释。</span><span class="sxs-lookup"><span data-stu-id="f398a-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="f398a-110">基于注释的帮助的每个部分都由关键字定义，每个关键字前面有一个句点（.）。</span><span class="sxs-lookup"><span data-stu-id="f398a-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="f398a-111">关键字可以按任意顺序出现。</span><span class="sxs-lookup"><span data-stu-id="f398a-111">The keywords can appear in any order.</span></span> <span data-ttu-id="f398a-112">关键字名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f398a-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="f398a-113">注释块必须包含至少一个 help 关键字。</span><span class="sxs-lookup"><span data-stu-id="f398a-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="f398a-114">例如，某些关键字可以在同一注释块中出现多次。</span><span class="sxs-lookup"><span data-stu-id="f398a-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="f398a-115">每个关键字的帮助内容都从关键字后面的行开始，可以跨多行。</span><span class="sxs-lookup"><span data-stu-id="f398a-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="f398a-116">基于注释的帮助主题中的所有行都必须是连续的。</span><span class="sxs-lookup"><span data-stu-id="f398a-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="f398a-117">如果基于注释的帮助主题遵循的注释不是帮助主题的一部分，则最后一个非帮助注释行与基于注释的帮助的开头之间必须至少有一个空白行。</span><span class="sxs-lookup"><span data-stu-id="f398a-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="f398a-118">例如，下面的基于注释的帮助主题包含。Description 关键字及其值，这是对函数或脚本的描述。</span><span class="sxs-lookup"><span data-stu-id="f398a-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```