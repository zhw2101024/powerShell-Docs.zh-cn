---
title: 用于配置的控件（格式）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364786"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)

指定一组使用此控件定义的 .NET 类型。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for 元素 for for SelectionSetName for control for control （Format）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

每个控件定义都必须定义至少一个类型名称、选择集或选择条件。

当要定义在多个视图中使用的一组对象时，通常使用选择集。 有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
