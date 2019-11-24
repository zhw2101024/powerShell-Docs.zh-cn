---
title: SelectionSet 的类型元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367956"
---
# <a name="types-element-for-selectionset-format"></a>Types Element for SelectionSet (Format)

定义选择集中的 .NET 对象。

配置元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）类型元素（格式）

## <a name="syntax"></a>语法

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Types` 元素的属性、子元素和父元素。 必须至少有一个子元素，但对于可添加的子元素数没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[类型的 TypeName 元素（格式）](./typename-element-for-types-format.md)|必需的元素。<br /><br /> 指定属于选择集的 .NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素（格式）](./selectionset-element-format.md)|定义一组可由集名称引用的 .NET 对象。|

## <a name="remarks"></a>备注

此元素定义的对象构成一个选项集，该选项集可由视图、视图定义（视图可以有多个定义）或指定选择条件时使用。  有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

此示例演示一个定义四个 .NET 类型的 `SelectionSet` 元素。

```xml
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

[定义对象集](./defining-selection-sets.md)

[SelectionSet 元素（格式）](./selectionset-element-format.md)

[类型的 TypeName 元素（格式）](./typename-element-for-types-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
