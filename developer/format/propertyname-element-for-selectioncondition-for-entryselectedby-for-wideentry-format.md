---
title: PropertyName 元素为 WideEntry （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860413"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)

指定触发条件的.NET 属性。 存在此属性时或当计算结果为`true`、 满足该条件，以及使用该定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 WideEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定义必须存在要使用此定义的条件。|

## <a name="text-value"></a>文本值

指定.NET 属性名称。

## <a name="remarks"></a>备注

选择条件必须指定至少一个属性名称或脚本来评估，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。

有关较宽的视图的其他组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
