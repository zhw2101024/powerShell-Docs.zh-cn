---
title: ViewSelectedBy 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368256"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName Element for ViewSelectedBy (Format)

指定视图显示的一组 .NET 对象。

ViewSelectedBy 的 Configuration 元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（format） SelectionSetName 元素（format）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)|定义视图显示的 .NET 对象。|

## <a name="text-value"></a>文本值

为选择集指定由 `Name` 元素定义的选择集的名称。

## <a name="remarks"></a>备注

如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。 有关定义和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示如何为列表视图指定选择集。 表、宽视图和自定义视图使用相同的架构。

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>另请参阅

[定义选择集](./defining-selection-sets.md)

[ViewSelectedBy 元素（格式）](./viewselectedby-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
