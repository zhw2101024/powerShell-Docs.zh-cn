---
title: 如何将注释添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862263"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加备注

本部分介绍如何添加 Windows PowerShell® cmdlet 帮助主题的备注部分。 说明部分用于解释不适合轻松地为其他结构化部分，如参数的更详细的说明的详细信息。 此内容可能包括对特定的提供程序时，该 cmdlet 的工作原理、 一些唯一的但却很重要，使用的 cmdlet 或避免出现的错误情况的方法的注释。

时，可以将它们添加到说明部分的说明的数量没有限制。 对于每个说明，添加一对\<maml:alert > 标记，用于\<maml:alertset > 节点。 每个需要注意的内容添加一组内\<maml:para > 标记。 使用空白\<maml:para > 标记的间距。

下面的 XML 演示\<maml:alertset > 具有这两个说明节点。 请注意，每个注释包含一个可选\<maml:title > 标记 (标题可用于任何组的分组\<maml:alert > 标记)，并且每个说明具有一个空行间距的内容之后。

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



