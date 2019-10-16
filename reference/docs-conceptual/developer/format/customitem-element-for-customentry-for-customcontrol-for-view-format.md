---
title: 用于 CustomControl for View （Format）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363946"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem Element for CustomEntry for CustomControl for View (Format)

定义自定义控件视图显示的数据及其显示方式。 定义自定义控件视图时，将使用此元素。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素CustomEntry for View （Format）

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
|[用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义控件显示的数据。|
|[View 的 CustomItem for CustomControl 的 Frame 元素（Format）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义自定义控件视图显示的数据及其显示方式。|
|[用于视图的自定义控件的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 向控件的显示添加一个空白行。|
|[View 的 CustomItem for CustomControl 的 Text 元素（Format）](./text-element-for-customitem-for-customview-for-view-format.md)|可选元素。<br /><br /> 指定由控件显示的数据的附加文本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于 View 的 CustomControl 的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自定义控件视图的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[用于视图的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[用于 View 的 CustomControl 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[View 的 CustomItem for CustomControl 的 Frame 元素（Format）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[用于 View 的 CustomItem for CustomControl 的换行符元素（格式）](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[View 的 CustomItem for CustomControl 的 Text 元素（Format）](./text-element-for-customitem-for-customview-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
