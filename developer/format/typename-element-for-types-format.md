---
title: TypeName 元素的类型 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083784"
---
# <a name="typename-element-for-types-format"></a>TypeName Element for Types (Format)

指定属于所选内容集的对象的.NET 类型。

配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 类型元素 （格式） 类型名称元素的类型 （格式）

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。 至少一个`TypeName`元素必须包含在选择集中。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[类型元素 （格式）](./types-element-for-selectionset-format.md)|定义集内所选内容的.NET 对象。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称。

## <a name="remarks"></a>备注

当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。 在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。

常见的选项集，由其名称定义的格式设置文件的视图时指定。 在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`元素为视图指定组。 但是，视图的不同项还可以指定适用于只有该视图的项的选择集。 有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示`SelectionSet`定义四种.NET 类型的元素。

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>另请参阅

[定义的选项集](./defining-selection-sets.md)

[SelectionSet 元素 （格式）](./selectionset-element-format.md)

[SelectionSets 元素 （格式）](./selectionsets-element-format.md)

[类型元素 （格式）](./types-element-for-selectionset-format.md)

[编写 Windows PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
