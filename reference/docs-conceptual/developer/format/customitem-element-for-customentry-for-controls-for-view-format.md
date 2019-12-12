---
title: 用于视图（格式）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363936"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem Element for CustomEntry for Controls for View (Format)

定义控件显示的数据及其显示方式。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format）元素 for CustomEntry 的控件

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。 有关详细信息，请参阅备注。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义控件显示的数据。|
|[用于视图的控件的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义数据的显示方式，例如，将数据向左或向右移动。|
|[用于视图的控件的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 向控件的显示添加一个空白行。|
|[用于视图的控件的 CustomItem 的文本元素（格式）](./text-element-for-customitem-for-controls-for-view-format.md)|可选元素。<br /><br /> 向控件的显示添加文本，如括号或方括号。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

指定 `CustomItem` 元素的子元素时，请记住以下事项：

- 必须按以下顺序添加子元素： `ExpressionBinding`、`NewLine`、`Text`和 `Frame`。

- 您可以指定的序列数量没有最大限制。

- 在每个序列中，可使用的 `ExpressionBinding` 元素数没有最大限制。

## <a name="see-also"></a>另请参阅

[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[用于视图的控件的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-view-format.md)

[用于视图的控件的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-controls-for-view-format.md)

[用于视图的控件的 CustomItem 的文本元素（格式）](./text-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
