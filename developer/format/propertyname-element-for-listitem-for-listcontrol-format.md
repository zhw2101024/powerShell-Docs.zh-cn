---
title: PropertyName ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855733"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName Element for ListItem for ListControl (Format)

指定其值显示在列表中的.NET 属性。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） Listitem 元素 （格式） ListItem 元素 （格式） 属性名称的配置元素ListItem （格式）

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="text-value"></a>文本值

指定显示其值的属性的名称。

## <a name="remarks"></a>备注

当指定此元素时，不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。

除了显示的属性值，还可以指定的值或可用于更改值的显示格式字符串的标签。 在列表视图中指定数据的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何以指定的标签和其值显示的属性。

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另请参阅

[ListControl （格式） 的列表项的脚本块元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[ListControl(Format) 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
