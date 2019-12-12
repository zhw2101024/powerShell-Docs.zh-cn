---
title: EnumerableExpansion （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368326"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)

指定通过此定义扩展的 .NET 类型集。

用于 EnumerableExpansion 的 SelectionSetName （Format） EntrySelectedBy 元素的配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（format） EntrySelectedBy 元素EnumerableExpansion （格式）

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
|[EnumerableExpansion 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)|定义通过此定义扩展的 .NET 集合对象。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

每个定义必须指定一个或多个类型名称、选择集或选择条件。

当要定义在多个视图中使用的一组对象时，通常使用选择集。 例如，您可能希望为同一组对象创建表视图和列表视图。 有关定义选择集的详细信息，请参阅为[视图定义对象集](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[定义选择集](./defining-selection-sets.md)

[EnumerableExpansion 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
