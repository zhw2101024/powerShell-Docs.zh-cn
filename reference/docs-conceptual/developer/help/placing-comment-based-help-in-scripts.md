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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361176"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="3bdf1-102">在脚本中放置基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="3bdf1-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="3bdf1-103">本主题介绍在何处放置脚本的基于注释的帮助，以便 `Get-Help` cmdlet 将基于注释的帮助主题与脚本关联，而不是与脚本中可能包含的任何函数关联。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="3bdf1-104">在何处放置脚本的基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="3bdf1-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="3bdf1-105">位于脚本文件的开头。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-105">At the beginning of the script file.</span></span> <span data-ttu-id="3bdf1-106">脚本帮助的前面只能是注释和空行。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="3bdf1-107">脚本文件末尾。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-107">At the end of the script file.</span></span>

  <span data-ttu-id="3bdf1-108">如果脚本正文中的第一项（帮助下的第一项）是函数声明，则脚本的末尾和函数声明之间必须至少有两个空行。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="3bdf1-109">否则，"帮助" 将被解释为该函数的帮助，而不是脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="3bdf1-110">脚本中帮助位置的示例</span><span class="sxs-lookup"><span data-stu-id="3bdf1-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="3bdf1-111">下面的示例显示了每个用于脚本的基于注释的帮助的放置选项。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="3bdf1-112">脚本开始的帮助</span><span class="sxs-lookup"><span data-stu-id="3bdf1-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="3bdf1-113">下面的示例显示了脚本开始时的注释。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="3bdf1-114">脚本结束时的帮助</span><span class="sxs-lookup"><span data-stu-id="3bdf1-114">Help at the End of a Script</span></span>

 <span data-ttu-id="3bdf1-115">下面的示例显示了脚本结束时的注释。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```