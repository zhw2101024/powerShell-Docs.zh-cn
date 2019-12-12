---
title: ListControl 的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365186"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition Element for ListItem for ListControl (Format)

定义要使用此列表项必须存在的条件。

用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ListItems for ListControl （Format） ItemSelectionCondition 元素的 ListControl （格式） "" 元素（格式）

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ItemSelectionCondition 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListItems 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定义其值显示在列表视图的行中的属性或脚本。|

## <a name="remarks"></a>备注

您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[ListControl 的 ListItems 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl 的 ItemSelectionCondition 的 PropertyName 元素（Format）](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
