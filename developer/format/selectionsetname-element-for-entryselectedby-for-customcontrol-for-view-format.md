---
title: SelectionSetName 元素的视图 （格式） 的 CustomControl EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855023"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)

指定一组.NET 对象列表项。 可以为一个条目指定的所选内容集的数量没有限制。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry EntrySelectedBy CustomEntry （格式） 的视图 （格式） SelectionSetName 元素的元素

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
|[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此自定义项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

自定义控件的每个条目必须具有至少一个类型名称、 选择集或定义的选择条件。

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 例如，你可能想要创建的表视图和同一组对象的列表视图。 有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。

有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomEntry EntrySelectedBy 元素](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[自定义控件视图](./creating-custom-controls.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
