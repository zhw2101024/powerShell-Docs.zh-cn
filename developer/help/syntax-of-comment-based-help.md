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

 基于注释的帮助编写为一系列的注释。 您可以在每行注释之前, 键入注释符号 （#） 也可以使用"\<#"和"#>"符号创建注释块。 注释块中的所有行被都解释为注释。

 由一个关键字定义的基于注释的帮助每个部分，每个关键字前面是句点 （.）。 关键字可以按任何顺序出现。 关键字名称不区分大小写。

 注释块必须包含至少一个帮助关键字。 某些关键字，如示例中，可以在相同的注释块中出现多次。 为每个关键字的帮助内容的关键字后的行上开始，并可以跨多个行。

 所有基于注释的帮助主题中的行必须是连续的。 如果基于注释的帮助主题后跟注释不是帮助的帮助主题的一部分，必须是帮助的最后一个非帮助注释行和基于注释的开头之间的至少一个空白行。

 例如，包含以下基于注释的帮助主题。描述关键字和其值，该值是函数或脚本的说明。

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```