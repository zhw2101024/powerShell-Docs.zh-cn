---
title: 使用 ListControl （格式） 的列表项的标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065421"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label Element for ListItem for ListControl (Format)

指定属性或脚本值的行中的左侧显示的标签。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） 的 ListControl 元素 （ListEntry 的 ListControl （格式） ListItems ListEntry 元素ListItems ListControl （格式） 标签 ListControl （格式） 的 ListItem 元素的格式） ListItem 元素

## <a name="syntax"></a>语法

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Label`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListItems 的 ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="text-value"></a>文本值

指定要向属性或脚本值的左侧显示的标签。

## <a name="remarks"></a>备注

如果未指定一个标签，显示属性或脚本的名称。 有关使用列表视图中的标签的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何将标签添加到行。

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
