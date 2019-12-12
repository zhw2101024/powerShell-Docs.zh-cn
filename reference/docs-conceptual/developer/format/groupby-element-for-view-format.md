---
title: View 的 GroupBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363626"
---
# <a name="groupby-element-for-view-format"></a>GroupBy Element for View (Format)

定义如何显示新的对象组。 定义表、列表、宽或自定义控件视图时，将使用此元素。

View 元素（format） ViewDefinitions 元素（format） View 元素（format） GroupBy 元素（Format）

## <a name="syntax"></a>语法

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>属性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素（Format）](./customcontrol-element-for-groupby-format.md)|可选元素。<br /><br /> 定义显示新组的自定义控件。|
|[GroupBy 的 CustomControlName 元素（Format）](./customcontrolname-element-for-groupby-format.md)|可选元素。<br /><br /> 指定用于显示新组的控件的名称。|
|[GroupBy 的标签元素（格式）](./label-element-for-groupby-format.md)|可选元素。<br /><br /> 指定在遇到新组时显示的标签。|
|[GroupBy 的 PropertyName 元素（Format）](./propertyname-element-for-groupby-format.md)|可选元素。<br /><br /> 指定 .NET 属性，在新组的值发生更改时启动新组。|
|[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)|可选元素。<br /><br /> 指定在新组的值发生更改时启动新组的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义一个视图，该视图显示一个或多个 .NET 对象。|

## <a name="remarks"></a>备注

定义如何显示新的对象组时，您必须指定将启动新组的属性或脚本。但是，不能同时指定两者。

## <a name="see-also"></a>另请参阅

[GroupBy 的 CustomControlName 元素（Format）](./customcontrolname-element-for-groupby-format.md)

[GroupBy 的标签元素（格式）](./label-element-for-groupby-format.md)

[GroupBy 的 PropertyName 元素（Format）](./propertyname-element-for-groupby-format.md)

[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)

[View 元素（格式）](./view-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
