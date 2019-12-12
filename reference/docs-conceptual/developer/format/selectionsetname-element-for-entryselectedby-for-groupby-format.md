---
title: GroupBy （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364736"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>SelectionSetName Element for EntrySelectedBy for GroupBy (Format)

为列表条目指定一组 .NET 对象。 对于可为条目指定的选项集数没有限制。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format） SelectionSetName 元素 for GroupBy （Format）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-groupby-format.md)|定义使用此自定义项的 .NET 类型或此项要使用的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

每个自定义控件定义都必须定义至少一个类型名称、选择集或选择条件。

当要定义在多个视图中使用的一组对象时，通常使用选择集。 例如，您可能希望为同一组对象创建表视图和列表视图。 有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-groupby-format.md)

[创建自定义控件](./creating-custom-controls.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
