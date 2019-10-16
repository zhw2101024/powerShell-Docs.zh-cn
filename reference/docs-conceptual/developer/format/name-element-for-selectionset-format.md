---
title: SelectionSet 的 Name 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362666"
---
# <a name="name-element-for-selectionset-format"></a>Name Element for SelectionSet (Format)

指定用于引用选项集的名称。

配置元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式） SelectionSet 的 Name 元素（格式）

## <a name="syntax"></a>语法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `Name` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素（格式）](./selectionset-element-format.md)|定义一组可由集名称引用的 .NET 对象。|

## <a name="text-value"></a>文本值

指定名称以引用选项集。 对于可使用哪些字符没有任何限制。

## <a name="remarks"></a>备注

此处指定的名称用于 `SelectionSetName` 元素。 视图可以使用的选项集，通过视图的定义（视图可以有多个定义），或指定选择条件。 有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

此示例演示一个定义四个 .NET 类型的 @no__t 0 元素。 选择集的名称为 "FileSystemTypes"。

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

[定义选择集](./defining-selection-sets.md)

[SelectionSet 元素（格式）](./selectionset-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
