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
# <a name="placing-comment-based-help-in-functions"></a>在函数中放置基于注释的帮助

本主题介绍在何处放置有关某个函数基于注释的帮助，以便`Get-Help`cmdlet 将基于注释的帮助主题与正确的函数相关联。

## <a name="where-to-place-comment-based-help-for-a-function"></a>有关某个函数基于注释的帮助的放置位置

- 在函数体的开头。

- 在函数体的末尾。

- 之前`Function`关键字。 将脚本或脚本模块中函数时，不能有多个空行之间的最后一行的基于注释的帮助和`Function`关键字。 否则为`Get-Help`脚本而不是该函数将帮助相关联。

## <a name="examples-of-help-placement-in-a-function"></a>帮助放置在函数中的示例

 下面的示例显示每个函数基于注释的帮助的三个放置选项。

### <a name="help-at-the-beginning-of-a-function-body"></a>在函数体开头帮助

 下面的示例演示基于注释的函数体的开头。

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

### <a name="help-at-the-end-of-a-function-body"></a>帮助函数体的末尾

 下面的示例演示基于注释的末尾的函数体。

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

### <a name="help-before-the-function-keyword"></a>在 Function 关键字之前帮助

 下面的示例显示了基于注释的 function 关键字之前的行上。

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```