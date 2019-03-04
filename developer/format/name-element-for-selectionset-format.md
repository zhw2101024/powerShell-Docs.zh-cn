---
title: SelectionSet （格式） 的名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858163"
---
# <a name="name-element-for-selectionset-format"></a>Name Element for SelectionSet (Format)

指定用来引用所选内容集的名称。

配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 的名称元素更改为的 SelectionSet （格式）

## <a name="syntax"></a>语法

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`Name`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 （格式）](./selectionset-element-format.md)|定义集的名称，可以引用.NET 对象的单个组。|

## <a name="text-value"></a>文本值

指定要引用所选内容集的名称。 有可以使用哪些字符没有限制。

## <a name="remarks"></a>备注

此处指定的名称中使用`SelectionSetName`元素。 可由视图定义的视图的选项集 （视图可以具有多个定义），或指定选择条件时。 有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

此示例显示了`SelectionSet`定义四种.NET 类型的元素。 所选内容集的名称是"FileSystemTypes"。

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

[定义的选项集](./defining-selection-sets.md)

[SelectionSet 元素 （格式）](./selectionset-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
