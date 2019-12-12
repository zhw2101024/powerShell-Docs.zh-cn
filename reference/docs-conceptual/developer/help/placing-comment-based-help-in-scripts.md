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
# <a name="placing-comment-based-help-in-scripts"></a>在脚本中放置基于注释的帮助

本主题介绍在何处放置脚本的基于注释的帮助，以便 `Get-Help` cmdlet 将基于注释的帮助主题与脚本关联，而不是与脚本中可能包含的任何函数关联。

## <a name="where-to-place-comment-based-help-for-a-script"></a>在何处放置脚本的基于注释的帮助

- 位于脚本文件的开头。 脚本帮助的前面只能是注释和空行。

- 脚本文件末尾。

  如果脚本正文中的第一项（帮助下的第一项）是函数声明，则脚本的末尾和函数声明之间必须至少有两个空行。 否则，"帮助" 将被解释为该函数的帮助，而不是脚本的帮助。

## <a name="examples-of-help-placement-in-a-script"></a>脚本中帮助位置的示例

 下面的示例显示了每个用于脚本的基于注释的帮助的放置选项。

### <a name="help-at-the-beginning-of-a-script"></a>脚本开始的帮助

 下面的示例显示了脚本开始时的注释。

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>脚本结束时的帮助

 下面的示例显示了脚本结束时的注释。

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```