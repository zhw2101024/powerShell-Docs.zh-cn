---
title: WideControl 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859823"
---
# <a name="widecontrol-element-format"></a>WideControl Element (Format)

定义范围内 （单个值） 的视图的列表格式。 此视图显示单个属性值或为每个对象的脚本值。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式）

## <a name="syntax"></a>语法

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`WideControl`元素。 不能指定`AutoSize`和`ColumnNumber`元素出现在同一时间。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl （格式） 的自动调整大小元素](./autosize-element-for-widecontrol-format.md)|可选元素。<br /><br /> 指定列的大小和列数会调整基于数据的大小。|
|[ColumnNumber WideControl （格式） 的元素](./columnnumber-element-for-widecontrol-format.md)|可选元素。<br /><br /> 指定宽视图中显示的列数。|
|[WideEntries 元素 （格式）](./wideentries-element-for-widecontrol-format.md)|必需的元素。<br /><br /> 提供了宽的视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义用于显示一个或多个.NET 对象的视图。|

## <a name="remarks"></a>备注

在定义较宽的视图，你可以添加`AutoSize`元素或`ColumnNumber`但不能添加两者。

在大多数情况下，只有一个定义需要为每个宽的视图，但可以有多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。 在这些情况下，可以为每个对象或对象集提供一个单独的定义。

有关较宽的视图的组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示`WideControl`用来显示的属性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl （格式） 的自动调整大小元素](./autosize-element-for-widecontrol-format.md)

[ColumnNumber WideControl （格式） 的元素](./columnnumber-element-for-widecontrol-format.md)

[视图元素 （格式）](./view-element-format.md)

[WideEntries 元素 （格式）](./wideentries-element-for-widecontrol-format.md)

[宽的视图 (Basic)](./wide-view-basic.md)

[创建较宽的视图](./creating-a-wide-view.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
