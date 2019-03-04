---
title: ItemSelectionCondition ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861863"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition Element for ListItem for ListControl (Format)

定义必须存在要使用此列表项的条件。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListControl （格式） ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的.NET 属性。|
|[ItemSelectionCondition 的 ListControl （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListItems 的 ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)|定义属性或其值显示在列表视图的行中的脚本。|

## <a name="remarks"></a>备注

您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。

## <a name="see-also"></a>另请参阅

[ListItems 的 ListControl （格式） 的 ListItem 元素](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl （格式） 的 ItemSelectionCondition PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition 的 ListControl （格式） 的脚本块元素](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
