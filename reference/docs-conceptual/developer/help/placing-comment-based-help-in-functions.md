---
title: 在函数中放置基于注释的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367776"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="fc591-102">在函数中放置基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="fc591-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="fc591-103">本主题介绍在何处放置函数的基于注释的帮助，以便 `Get-Help` cmdlet 将基于注释的帮助主题与正确的函数相关联。</span><span class="sxs-lookup"><span data-stu-id="fc591-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="fc591-104">在何处放置函数的基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="fc591-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="fc591-105">函数体的开头。</span><span class="sxs-lookup"><span data-stu-id="fc591-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="fc591-106">函数体的末尾。</span><span class="sxs-lookup"><span data-stu-id="fc591-106">At the end of the function body.</span></span>

- <span data-ttu-id="fc591-107">在 `Function` 关键字之前。</span><span class="sxs-lookup"><span data-stu-id="fc591-107">Before the `Function` keyword.</span></span> <span data-ttu-id="fc591-108">当函数在脚本或脚本模块中时，基于注释的帮助的最后一行与 `Function` 关键字之间不能有多个空行。</span><span class="sxs-lookup"><span data-stu-id="fc591-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="fc591-109">否则，`Get-Help` 会将帮助与脚本相关联，而不是与函数相关联。</span><span class="sxs-lookup"><span data-stu-id="fc591-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="fc591-110">函数中帮助位置的示例</span><span class="sxs-lookup"><span data-stu-id="fc591-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="fc591-111">下面的示例显示了三个位置选项中的每一个选项，用于为函数提供基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="fc591-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="fc591-112">函数体开始的帮助</span><span class="sxs-lookup"><span data-stu-id="fc591-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="fc591-113">下面的示例显示了函数体开头的注释。</span><span class="sxs-lookup"><span data-stu-id="fc591-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="fc591-114">函数体末尾的帮助</span><span class="sxs-lookup"><span data-stu-id="fc591-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="fc591-115">下面的示例显示了函数体末尾的注释。</span><span class="sxs-lookup"><span data-stu-id="fc591-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="fc591-116">函数关键字之前的帮助</span><span class="sxs-lookup"><span data-stu-id="fc591-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="fc591-117">下面的示例显示了基于函数关键字之前的行的注释。</span><span class="sxs-lookup"><span data-stu-id="fc591-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```