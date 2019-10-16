---
title: 如何将相关链接添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361216"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加相关链接

本部分介绍如何添加对与 Windows PowerShell® cmdlet 帮助主题相关的其他内容的引用。 由于这些引用显示在命令窗口中，因此它们不会直接链接到引用的内容。

在 Windows PowerShell®中包含的 cmdlet 帮助主题中，这些链接引用其他 cmdlet、概念内容（"about_"）以及其他与 Windows PowerShell®无关的文档和帮助文件。

下面的 XML 演示如何将包含两个引用的 RelatedLinks 节点添加到相关主题。

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



