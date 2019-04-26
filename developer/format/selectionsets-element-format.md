---
title: SelectionSets 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063755"
---
# <a name="selectionsets-element-format"></a>SelectionSets Element (Format)

定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。 视图和控件的格式设置文件可以通过使用仅所选内容集的名称引用对象的完整的集合。

配置元素 SelectionSets 元素格式

## <a name="syntax"></a>语法

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`SelectionSets`元素。 每个子元素定义一组的集的名称，可以引用的对象。 子元素的顺序并不重要。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[SelectionSet 元素 （格式）](./selectionset-element-format.md)|必需的元素。<br /><br /> 定义集的名称，可以引用.NET 对象的单个组。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置元素](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。 在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。

常见的选项集，由其名称定义的格式设置文件的视图或视图的定义时指定。 在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集。 有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="see-also"></a>另请参阅

[配置元素](./configuration-element-format.md)

[定义的选项集](./defining-selection-sets.md)

[SelectionSet 元素 （格式）](./selectionset-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
