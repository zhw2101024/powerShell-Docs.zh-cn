---
title: GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064061"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>SelectionSetName Element for EntrySelectedBy for GroupBy (Format)

指定一组.NET 对象列表项。 可以为一个条目指定的所选内容集的数量没有限制。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl GroupBy （格式） 的 GroupBy （格式） 的 GroupBy （格式） 的 EntrySelectedBy SelectionSetName 元素 CustomEntry EntrySelectedBy 元素

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)|定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

每个自定义控件定义必须至少一个类型名称、 选择集或定义的选择条件。

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 例如，你可能想要创建的表视图和同一组对象的列表视图。 有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。

有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-groupby-format.md)

[创建自定义控件](./creating-custom-controls.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
