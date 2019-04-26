---
title: ListControl （格式） 的列表项的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064571"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock Element for ListItem for ListControl (Format)

指定其值显示的行中的脚本。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListControl （格式） ScriptBlock ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListItem 元素 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="text-value"></a>文本值

指定其值显示的行中的脚本。

## <a name="remarks"></a>备注

当指定此元素时，不能指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

在列表视图中指定脚本的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

下面的示例演示如何指定其值显示的属性。

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>另请参阅

[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[ListItems 的 ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
