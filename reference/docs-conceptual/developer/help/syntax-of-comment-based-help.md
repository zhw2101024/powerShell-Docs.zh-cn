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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367756"
---
# <a name="syntax-of-comment-based-help"></a>基于注释的帮助的语法

本部分介绍基于注释的帮助的语法。

## <a name="syntax-diagram"></a>语法关系图

 基于注释的帮助的语法如下所示：

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>语法说明

 基于注释的帮助以一系列注释形式编写。 您可以在每行注释之前键入注释符号（#），也可以使用 "\< #" 和 "# >" 符号创建注释块。 注释块内的所有行都解释为注释。

 基于注释的帮助的每个部分都由关键字定义，每个关键字前面有一个句点（.）。 关键字可以按任意顺序出现。 关键字名称不区分大小写。

 注释块必须包含至少一个 help 关键字。 例如，某些关键字可以在同一注释块中出现多次。 每个关键字的帮助内容都从关键字后面的行开始，可以跨多行。

 基于注释的帮助主题中的所有行都必须是连续的。 如果基于注释的帮助主题遵循的注释不是帮助主题的一部分，则最后一个非帮助注释行与基于注释的帮助的开头之间必须至少有一个空白行。

 例如，下面的基于注释的帮助主题包含。Description 关键字及其值，这是对函数或脚本的描述。

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```