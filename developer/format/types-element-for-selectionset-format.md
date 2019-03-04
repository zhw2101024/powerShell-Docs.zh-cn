---
title: 元素类型为 SelectionSet （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862373"
---
# <a name="types-element-for-selectionset-format"></a>Types Element for SelectionSet (Format)

定义集内所选内容的.NET 对象。

配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 类型元素 （格式）

## <a name="syntax"></a>语法

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`Types`元素。 必须有至少一个子元素，但没有可添加的子元素的数目没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TypeName 元素的类型 （格式）](./typename-element-for-types-format.md)|必需的元素。<br /><br /> 指定属于所选内容集的.NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 元素 （格式）](./selectionset-element-format.md)|定义一组的集的名称，可以引用.NET 对象。|

## <a name="remarks"></a>备注

此元素定义的对象构成了可由视图定义的视图的选择集 （视图可以具有多个定义），或指定选择条件时。  有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

此示例显示了`SelectionSet`定义四种.NET 类型的元素。

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

[定义对象的集](./defining-selection-sets.md)

[SelectionSet 元素 （格式）](./selectionset-element-format.md)

[TypeName 元素的类型 （格式）](./typename-element-for-types-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
