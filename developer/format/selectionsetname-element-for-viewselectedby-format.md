---
title: ViewSelectedBy （格式） 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076219"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName Element for ViewSelectedBy (Format)

指定一组.NET 对象所显示的视图。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ViewSelectedBy 元素 （格式） SelectionSetName 元素 ViewSelectedBy （格式）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)|定义视图所显示的.NET 对象。|

## <a name="text-value"></a>文本值

指定由定义的选项集的名称`Name`选项集的元素。

## <a name="remarks"></a>备注

当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。 有关定义和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示如何指定设置列表视图的选择。 相同的架构用于表中，宽，和自定义视图。

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

[定义的选项集](./defining-selection-sets.md)

[ViewSelectedBy 元素 （格式）](./viewselectedby-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
