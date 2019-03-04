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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860763"
---
# <a name="placing-comment-based-help-in-scripts"></a>在脚本中放置基于注释的帮助

本主题介绍在何处放置基于注释的帮助的脚本，以便`Get-Help`cmdlet 将基于注释的帮助主题相关联，使用脚本，而不可能在脚本中的任何函数。

## <a name="where-to-place-comment-based-help-for-a-script"></a>基于注释的帮助的脚本的放置位置

- 在脚本文件的开头。 只能通过注释和空白的行，可以在脚本中前面脚本帮助。

- 在脚本文件的末尾。

  如果在脚本正文 （之后帮助） 中的第一项是函数声明，必须至少两个脚本的帮助的末尾与函数声明之间的空行。 否则，帮助被解释为帮助对于函数，而不是脚本的帮助。

## <a name="examples-of-help-placement-in-a-script"></a>帮助放置在脚本中的示例

 下面的示例显示每个基于注释的帮助的脚本的放置选项。

### <a name="help-at-the-beginning-of-a-script"></a>在脚本开头帮助

 下面的示例演示基于注释的脚本的开头。

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>在脚本末尾帮助

 下面的示例演示基于注释的脚本的末尾。

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```