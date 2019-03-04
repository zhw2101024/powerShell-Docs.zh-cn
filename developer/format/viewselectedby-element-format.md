---
title: ViewSelectedBy 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863183"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy Element (Format)

定义视图所显示的.NET 对象。 每个视图都必须指定至少一个.NET 对象。

ViewDefinitions 元素 （格式） 视图元素 （格式） ViewSelectedBy 元素 （格式）

## <a name="syntax"></a>语法

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`ViewSelectedBy`元素。 此元素必须包含至少一个`TypeName`或`SelectionSetName`子元素。 可以指定的子元素的数目没有限制也不是其顺序重要。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy （格式） 的类型名称元素](./typename-element-for-viewselectedby-format.md)|可选元素。<br /><br /> 指定视图显示的.NET 对象。|
|[ViewSelectedBy （格式） 的 SelectionSetName 元素](./selectionsetname-element-for-viewselectedby-format.md)|可选元素。<br /><br /> 指定一组.NET 对象所显示的视图。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义一个视图，显示一个或多个.NET 对象。|

## <a name="remarks"></a>备注

有关如何在不同的视图中使用此元素的详细信息，请参阅[表视图组件](./creating-a-table-view.md)，[列表视图组件](./creating-a-list-view.md)，[宽视图组件](./creating-a-wide-view.md)，以及[自定义控件组件](./creating-custom-controls.md)。

`SelectionSetName`时的格式设置文件定义的对象的多个视图将显示一组使用元素。 有关如何定义和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示如何指定[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)列表视图的对象。 相同的架构用于表中，宽，和自定义视图。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[创建表视图](./creating-a-table-view.md)

[创建较宽的视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[定义的选项集](./defining-selection-sets.md)

[ViewSelectedBy （格式） 的 SelectionSetName 元素](./selectionsetname-element-for-viewselectedby-format.md)

[类型名称元素 （格式）](./typename-element-for-viewselectedby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
