---
title: 配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858133"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)

指定.NET 类型的触发器条件的集。 当存在任何此集中的类型时，满足该条件，并使用此控件显示该对象。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素SelectionCondition 的 Controls 的配置 （格式） 的配置 （格式） SelectionSetName 元素

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定义必须存在要使用的控件定义的条件。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。 有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

选择条件可以指定所选内容集或.NET 类型，但不能同时指定。 有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[定义何时显示数据的条件](./defining-conditions-for-displaying-data.md)

[定义的选项集](./defining-selection-sets.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
