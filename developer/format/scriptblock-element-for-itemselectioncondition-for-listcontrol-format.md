---
title: 脚本块元素 ListControl （格式） 的 ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855413"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock Element for ItemSelectionCondition for ListControl (Format)

指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。 定义列表视图时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListItem ListControl （格式） 的 ItemSelectionCondition ListControl （格式） 脚本块元素的列表控件 （格式） ItemSelectionCondition 元素 ListItems ListControl （格式） ListItem 元素

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|定义必须存在要使用此列表项的条件。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

如果使用此元素时，不能指定`PropertyName`元素定义的选择条件时。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
