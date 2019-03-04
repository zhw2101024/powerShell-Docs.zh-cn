---
title: 如何将相关的链接添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855393"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加相关链接

本部分介绍如何将引用添加到与 Windows PowerShell® cmdlet 帮助主题相关的其他内容。 在命令窗口中显示这些引用，因为它们不直接向引用的内容链接。

在 Windows PowerShell® 中包含的 cmdlet 帮助主题，这些链接引用其他 cmdlet、 概念性内容 ("about_") 和其他文档和与 Windows PowerShell® 不相关的帮助文件。

下面的 XML 演示如何添加一个包含两个引用相关主题的 RelatedLinks 节点。

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



