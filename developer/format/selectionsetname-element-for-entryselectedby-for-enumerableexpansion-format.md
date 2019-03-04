---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862743"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)

指定.NET 类型的情况下此定义展开的组。

用于为 EntrySelectedBy EnumerableExpansion （格式） SelectionSetName 元素的配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式） EntrySelectedBy 元素EnumerableExpansion （格式）

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
|[EnumerableExpansion （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-enumerableexpansion-format.md)|定义此定义的扩展的.NET 集合对象。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

每个定义必须指定一个或多个类型名称、 一个选择集或选择条件。

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 例如，你可能想要创建的表视图和同一组对象的列表视图。 有关定义的选项集的详细信息，请参阅[定义设置的对象图](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[定义的选项集](./defining-selection-sets.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-enumerableexpansion-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
