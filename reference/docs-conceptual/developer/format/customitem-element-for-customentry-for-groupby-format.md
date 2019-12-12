---
title: GroupBy （Format）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363876"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem Element for CustomEntry for GroupBy (Format)

定义自定义控件视图显示的数据及其显示方式。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomEntry for GroupBy （Format）

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 定义控件显示的数据。|
|[GroupBy 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 定义自定义控件视图显示的数据及其显示方式。|
|[GroupBy 的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 向控件的显示添加一个空白行。|
|[GroupBy 的 CustomItem 文本元素（格式）](./text-element-for-customitem-for-groupby-format.md)|可选元素。<br /><br /> 指定由控件显示的数据的附加文本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)|提供自定义控件视图的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[GroupBy 的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy 的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy 的 CustomItem 文本元素（格式）](./text-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
