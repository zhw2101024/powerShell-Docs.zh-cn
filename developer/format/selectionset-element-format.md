---
title: SelectionSet 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076304"
---
# <a name="selectionset-element-format"></a>SelectionSet Element (Format)

定义一组的集的名称，可以引用.NET 对象。

配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式）

## <a name="syntax"></a>语法

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSet`元素。 每个所选内容集必须具有一个名称，并且它必须指定集的.NET 对象。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[SelectionSet （格式） 的名称元素](./name-element-for-selectionset-format.md)|必需的元素。<br /><br /> 指定用来引用所选内容集的名称。|
|[类型元素 （格式）](./types-element-for-selectionset-format.md)|必需的元素。<br /><br /> 定义集内所选内容的.NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。|

## <a name="remarks"></a>备注

当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。 在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。

常见的选项集，由其名称定义的格式设置文件的视图或视图的定义时指定。 在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集。 有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示`SelectionSet`定义四种.NET 类型的元素。

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

[Name 元素的 SelectionSet （格式）](./name-element-for-selectionset-format.md)

[SelectionSets 元素 （格式）](./selectionsets-element-format.md)

[类型元素 （格式）](./types-element-for-selectionset-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
