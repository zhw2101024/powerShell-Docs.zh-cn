---
title: SelectionSet 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368376"
---
# <a name="selectionset-element-format"></a>SelectionSet Element (Format)

定义一组可由集名称引用的 .NET 对象。

配置元素（格式） SelectionSets 元素（format） SelectionSet 元素（格式）

## <a name="syntax"></a>语法

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSet` 元素的属性、子元素和父元素。 每个选项集都必须具有一个名称，并且必须指定该集的 .NET 对象。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionSet 的 Name 元素（Format）](./name-element-for-selectionset-format.md)|必需的元素。<br /><br /> 指定用于引用选项集的名称。|
|[Types 元素（格式）](./types-element-for-selectionset-format.md)|必需的元素。<br /><br /> 定义选择集中的 .NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|定义可供格式设置文件的所有视图使用的常用 .NET 对象集。|

## <a name="remarks"></a>备注

如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。 定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。

常用选择集在定义格式设置文件的视图或视图定义时由其名称指定。 在这些情况下，`ViewSelectedBy` 和 `EntrySelectedBy` 元素的 `SelectionSetName` 子元素指定要使用的集。 有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示一个定义四个 .NET 类型的 `SelectionSet` 元素。

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

[SelectionSet 的 Name 元素（Format）](./name-element-for-selectionset-format.md)

[SelectionSets 元素（格式）](./selectionsets-element-format.md)

[Types 元素（格式）](./types-element-for-selectionset-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
