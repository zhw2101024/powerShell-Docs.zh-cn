---
title: 用于 CustomControl for View （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364746"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)

为列表条目指定一组 .NET 对象。 对于可为条目指定的选项集数没有限制。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedByCustomEntry 的 EntrySelectedBy 的 CustomEntry for View （Format） SelectionSetName 元素的元素

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
|[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此自定义项的 .NET 类型或此项要使用的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

每个自定义控件项必须至少定义一个类型名称、选择集或选择条件。

当要定义在多个视图中使用的一组对象时，通常使用选择集。 例如，您可能希望为同一组对象创建表视图和列表视图。 有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[自定义控件视图](./creating-custom-controls.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
