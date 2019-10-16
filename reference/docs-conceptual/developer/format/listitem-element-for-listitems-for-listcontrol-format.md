---
title: ListControl 的 ListItems 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365126"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem Element for ListItems for ListControl (Format)

定义其值显示在列表视图的行中的属性或脚本。

ListEntry 的 ListControl （format） ListControl 元素的配置元素（格式） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素（format）ListControl 元素的输入（格式）

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

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `ListItem` 元素的属性、子元素和父元素。 只能指定一个属性或脚本。

### <a name="attributes"></a>属性

无

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的的格式字符串元素（格式）](./formatstring-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定定义属性或脚本值显示方式的格式字符串。|
|[ListControl 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 定义要使用此列表项必须存在的条件。|
|[ListControl 的标记元素（格式）](./label-element-for-listitem-for-listcontrol-format.md)|可选元素<br /><br /> 指定在行的属性或脚本值左侧显示的标签。|
|[ListControl 的名称名称元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定其值显示在行中的 .NET 属性。|
|[ListControl 的的 ScriptBlock 元素（格式）](./scriptblock-element-for-listitem-for-listcontrol-format.md)|可选元素。<br /><br /> 指定其值在行中显示的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[List 控件的 ListItems 元素（Format）](./listitems-element-for-listentry-for-listcontrol-format.md)|定义其值在列表视图中显示的属性和脚本。|

## <a name="remarks"></a>备注

有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例显示了用于定义列表视图的三行的 XML 元素。 前两行显示 .NET 属性的值，最后一行显示脚本生成的值。

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

[ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[输入字符串的格式字符串元素（格式）](./formatstring-element-for-listitem-for-listcontrol-format.md)

[元素的 Label 元素（格式）](./label-element-for-listitem-for-listcontrol-format.md)

[元素名称元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)

[脚本块元素（格式）](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[创建列表视图](./creating-a-list-view.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
