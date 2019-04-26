---
title: 视图 （格式） 的 GroupBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065525"
---
# <a name="groupby-element-for-view-format"></a>GroupBy Element for View (Format)

定义新的一组对象的显示方式。 定义表、 列表、 宽，或自定义控件视图时，将使用此元素。

视图 （格式） 的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

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

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl 元素](./customcontrol-element-for-groupby-format.md)|可选元素。<br /><br /> 定义显示新组的自定义控件。|
|[GroupBy （格式） 的 CustomControlName 元素](./customcontrolname-element-for-groupby-format.md)|可选元素。<br /><br /> 指定控件用于显示新组的名称。|
|[GroupBy （格式） 的标签元素](./label-element-for-groupby-format.md)|可选元素。<br /><br /> 指定遇到新的组时显示的标签。|
|[GroupBy （格式） 的属性名称元素](./propertyname-element-for-groupby-format.md)|可选元素。<br /><br /> 指定在开始的.NET 属性及其值发生更改时的新组。|
|[GroupBy （格式） 的脚本块元素](./scriptblock-element-for-groupby-format.md)|可选元素。<br /><br /> 指定其值发生更改时启动新的组的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义一个视图，显示一个或多个.NET 对象。|

## <a name="remarks"></a>备注

在定义新的一组对象的显示方式时，必须指定属性或脚本将启动新的组;但是，您不能同时指定。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 CustomControlName 元素](./customcontrolname-element-for-groupby-format.md)

[GroupBy （格式） 的标签元素](./label-element-for-groupby-format.md)

[GroupBy （格式） 的属性名称元素](./propertyname-element-for-groupby-format.md)

[GroupBy （格式） 的脚本块元素](./scriptblock-element-for-groupby-format.md)

[视图元素 （格式）](./view-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
