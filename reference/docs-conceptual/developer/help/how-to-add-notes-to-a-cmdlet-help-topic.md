---
title: 如何向 Cmdlet 帮助主题添加注释 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361266"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加备注

本部分介绍如何向 Windows PowerShell® cmdlet 帮助主题添加注释部分。 "注释" 部分用于解释不能轻松地加入其他结构化部分的详细信息，如更详细的参数说明。 此内容可能包括有关 cmdlet 如何与特定提供程序一起使用的注释、对 cmdlet 的一些独特但重要的使用，或者用于避免可能的错误情况的方法。

可以添加到注释部分的便笺数量没有限制。 对于每个注释，请将一对 @no__t： > 标记添加到 \<maml： alertset > 节点。 每个注释的内容将添加到一组 @no__t 0maml： > 标记中。 使用空白 @no__t：段落 > 标记进行间距。

下面的 XML 显示了一个具有两个注释的 \<maml： alertset > 节点。 请注意，每个注释都有一个可选的 \<maml： title > 标记（标题可用于对任何一组 \<maml： alert > 标记）进行分组，并且每个注释的内容后均为空白行。

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



