---
title: SelectionSets 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361866"
---
# <a name="selectionsets-element-format"></a>SelectionSets Element (Format)

定义可供格式设置文件的所有视图使用的常用 .NET 对象集。 格式设置文件的视图和控件可以只使用选择集的名称来引用完整的对象集。

配置元素 SelectionSets 元素格式

## <a name="syntax"></a>语法

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `SelectionSets` 元素的属性、子元素和父元素。 每个子元素定义一组可由集名称引用的对象。 子元素的顺序并不重要。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素（格式）](./selectionset-element-format.md)|必需的元素。<br /><br /> 定义一组可由集名称引用的 .NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置元素](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。 定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。

常用选择集在定义格式设置文件的视图或视图定义时由其名称指定。 在这些情况下，@no__t 的 @no__t 子元素和 @no__t 2 元素指定要使用的集。 有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[配置元素](./configuration-element-format.md)

[定义选择集](./defining-selection-sets.md)

[SelectionSet 元素（格式）](./selectionset-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
