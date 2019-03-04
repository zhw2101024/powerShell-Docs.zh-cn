---
title: SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853213"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)

指定触发条件的脚本。 当此脚本的计算结果为`true`、 满足该条件，以及使用该定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry EntrySelectedBy 的 Controls 的配置 （格式） 的配置 （格式） SelectionCondition 元素的控件的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素SelectionCondition 的 Controls 的配置 （格式） 的脚本块元素

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
|[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定义必须存在要使用的常见控件定义的条件。|

## <a name="text-value"></a>文本值

指定计算的脚本。

## <a name="remarks"></a>备注

选择条件必须指定至少一个脚本或属性名称来评估，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
