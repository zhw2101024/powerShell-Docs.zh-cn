---
title: ViewSelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367966"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy Element (Format)

定义视图显示的 .NET 对象。 每个视图必须至少指定一个 .NET 对象。

ViewDefinitions 元素（格式） View 元素（Format） ViewSelectedBy 元素（Format）

## <a name="syntax"></a>语法

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `ViewSelectedBy` 元素的属性、子元素和父元素。 此元素必须包含至少一个 @no__t 0 或 @no__t 子元素。 对于可以指定的子元素数没有限制，也没有其顺序。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ViewSelectedBy 的 TypeName 元素（Format）](./typename-element-for-viewselectedby-format.md)|可选元素。<br /><br /> 指定视图显示的 .NET 对象。|
|[ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)|可选元素。<br /><br /> 指定视图显示的一组 .NET 对象。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义一个视图，该视图显示一个或多个 .NET 对象。|

## <a name="remarks"></a>备注

有关此元素在不同视图中的使用方式的详细信息，请参阅[表视图组件](./creating-a-table-view.md)、[列表视图](./creating-a-list-view.md)组件、[宽视图组件](./creating-a-wide-view.md)和[自定义控件组件](./creating-custom-controls.md)。

当格式设置文件定义一组由多个视图显示的对象时，将使用 @no__t 0 元素。 有关如何定义和引用选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。

## <a name="example"></a>示例

下面的示例演示如何为列表视图指定[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。 表、宽视图和自定义视图使用相同的架构。

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

[创建宽视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[定义选择集](./defining-selection-sets.md)

[ViewSelectedBy 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName 元素（格式）](./typename-element-for-viewselectedby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
