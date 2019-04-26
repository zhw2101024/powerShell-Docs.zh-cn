---
title: 在 Functions 中放置基于注释的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083189"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="5948c-102">在函数中放置基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="5948c-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="5948c-103">本主题介绍在何处放置有关某个函数基于注释的帮助，以便`Get-Help`cmdlet 将基于注释的帮助主题与正确的函数相关联。</span><span class="sxs-lookup"><span data-stu-id="5948c-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="5948c-104">有关某个函数基于注释的帮助的放置位置</span><span class="sxs-lookup"><span data-stu-id="5948c-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="5948c-105">在函数体的开头。</span><span class="sxs-lookup"><span data-stu-id="5948c-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="5948c-106">在函数体的末尾。</span><span class="sxs-lookup"><span data-stu-id="5948c-106">At the end of the function body.</span></span>

- <span data-ttu-id="5948c-107">之前`Function`关键字。</span><span class="sxs-lookup"><span data-stu-id="5948c-107">Before the `Function` keyword.</span></span> <span data-ttu-id="5948c-108">将脚本或脚本模块中函数时，不能有多个空行之间的最后一行的基于注释的帮助和`Function`关键字。</span><span class="sxs-lookup"><span data-stu-id="5948c-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="5948c-109">否则为`Get-Help`脚本而不是该函数将帮助相关联。</span><span class="sxs-lookup"><span data-stu-id="5948c-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="5948c-110">帮助放置在函数中的示例</span><span class="sxs-lookup"><span data-stu-id="5948c-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="5948c-111">下面的示例显示每个函数基于注释的帮助的三个放置选项。</span><span class="sxs-lookup"><span data-stu-id="5948c-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="5948c-112">在函数体开头帮助</span><span class="sxs-lookup"><span data-stu-id="5948c-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="5948c-113">下面的示例演示基于注释的函数体的开头。</span><span class="sxs-lookup"><span data-stu-id="5948c-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="5948c-114">帮助函数体的末尾</span><span class="sxs-lookup"><span data-stu-id="5948c-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="5948c-115">下面的示例演示基于注释的末尾的函数体。</span><span class="sxs-lookup"><span data-stu-id="5948c-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="5948c-116">在 Function 关键字之前帮助</span><span class="sxs-lookup"><span data-stu-id="5948c-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="5948c-117">下面的示例显示了基于注释的 function 关键字之前的行上。</span><span class="sxs-lookup"><span data-stu-id="5948c-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```