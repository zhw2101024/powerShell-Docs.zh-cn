---
title: 在脚本中放置基于注释的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083223"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="84e7e-102">在脚本中放置基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="84e7e-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="84e7e-103">本主题介绍在何处放置基于注释的帮助的脚本，以便`Get-Help`cmdlet 将基于注释的帮助主题相关联，使用脚本，而不可能在脚本中的任何函数。</span><span class="sxs-lookup"><span data-stu-id="84e7e-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="84e7e-104">基于注释的帮助的脚本的放置位置</span><span class="sxs-lookup"><span data-stu-id="84e7e-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="84e7e-105">在脚本文件的开头。</span><span class="sxs-lookup"><span data-stu-id="84e7e-105">At the beginning of the script file.</span></span> <span data-ttu-id="84e7e-106">只能通过注释和空白的行，可以在脚本中前面脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="84e7e-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="84e7e-107">在脚本文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="84e7e-107">At the end of the script file.</span></span>

  <span data-ttu-id="84e7e-108">如果在脚本正文 （之后帮助） 中的第一项是函数声明，必须至少两个脚本的帮助的末尾与函数声明之间的空行。</span><span class="sxs-lookup"><span data-stu-id="84e7e-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="84e7e-109">否则，帮助被解释为帮助对于函数，而不是脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="84e7e-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="84e7e-110">帮助放置在脚本中的示例</span><span class="sxs-lookup"><span data-stu-id="84e7e-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="84e7e-111">下面的示例显示每个基于注释的帮助的脚本的放置选项。</span><span class="sxs-lookup"><span data-stu-id="84e7e-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="84e7e-112">在脚本开头帮助</span><span class="sxs-lookup"><span data-stu-id="84e7e-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="84e7e-113">下面的示例演示基于注释的脚本的开头。</span><span class="sxs-lookup"><span data-stu-id="84e7e-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="84e7e-114">在脚本末尾帮助</span><span class="sxs-lookup"><span data-stu-id="84e7e-114">Help at the End of a Script</span></span>

 <span data-ttu-id="84e7e-115">下面的示例演示基于注释的脚本的末尾。</span><span class="sxs-lookup"><span data-stu-id="84e7e-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```