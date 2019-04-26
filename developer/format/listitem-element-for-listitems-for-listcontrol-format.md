---
title: ListItems 的 ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065761"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem Element for ListItems for ListControl (Format)

定义属性或其值显示在列表视图的行中的脚本。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素 ListControl （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素ListItem ListControl 元素 （格式）

## <a name="syntax"></a>语法

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`ListItem`元素。 可以指定只有一个属性或脚本。

### <a name="attributes"></a>属性

无

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[ListControl （格式） 的列表项的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定定义如何显示的属性或脚本的值的格式字符串。|
|[ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 定义必须存在要使用此列表项的条件。|
|[ListControl （格式） 的列表项的标签元素](./label-element-for-listitem-for-listcontrol-format.md)|可选元素<br /><br /> 指定属性或脚本值的行中的左侧显示的标签。|
|[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定其值显示的行中的.NET 属性。|
|[ListControl （格式） 的列表项的脚本块元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定其值显示的行中的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[列表控件 （格式） 的 Listitem 元素](./listitems-element-for-listentry-for-listcontrol-format.md)|定义属性和其值显示在列表视图中的脚本。|

## <a name="remarks"></a>备注

列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例演示定义列表视图的三个行的 XML 元素。 前两行显示.NET 属性的值，最后一行显示由脚本生成的值。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>另请参阅

[Listitem 元素 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[ListItem （格式） 的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的标签元素](./label-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的属性名称元素](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的脚本块元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
