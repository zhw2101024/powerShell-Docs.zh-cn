---
title: 类型的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368026"
---
# <a name="typename-element-for-types-format"></a>TypeName Element for Types (Format)

指定属于选择集的对象的 .NET 类型。

配置元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）类型元素（格式）类型的类型名称元素（格式）

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。 选择集中必须包含至少一个 `TypeName` 元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Types 元素（格式）](./types-element-for-selectionset-format.md)|定义选择集中的 .NET 对象。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名称。

## <a name="remarks"></a>备注

如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。 定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。

常用选择集在定义格式设置文件的视图时由其名称指定。 在这些情况下，视图的 `ViewSelectedBy` 元素的 `SelectionSetName` 子元素将指定集。 但是，视图的不同项还可以指定仅适用于该视图项的选择集。 有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示一个定义四个 .NET 类型的 `SelectionSet` 元素。

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

[定义选择集](./defining-selection-sets.md)

[SelectionSet 元素（格式）](./selectionset-element-format.md)

[SelectionSets 元素（格式）](./selectionsets-element-format.md)

[Types 元素（格式）](./types-element-for-selectionset-format.md)

[编写 Windows PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
